# Rails Controller
The primary responsibilty of controller is to accept a request, routes to the relevant objects and respond with the right view.
Controller is the connecting point between almost every other objects (such as views, models, etc).

In terms of Single Responsibility Principle (SRP), controller should only accept a request and respond correctly. 
The only logic in a controller should be how to respond correctly.

We follow the 'skinny controllers, fat models' principle. Hence, a controller's action should be as short as possible. A good guide is around 4 to 8 lines.

## Common Refactoring of Controllers
The main idea is to extract as much logic as possible from controller's action to keep it skinny.

We practise extracting `params` into its private methods so as to keep the controller action skinny and to decouple the params structure from the action.

Params should also be name spaced.
For example, the title field of a form to submit a comment should be name spaced under the model name `params[:comment][:title]`.

We also use [ActiveRecord concerns](http://api.rubyonrails.org/classes/ActiveSupport/Concern.html) to extract methods into concerns.

Code can be extracted into model if the logic concerns the model's responsibility.

## Routing
Following Rails convention, our routes should be RESTful.
Read more about [Rails routes](http://guides.rubyonrails.org/routing.html).

## Testing Controller
In controller testing, we focus on the "side effects" that calling a controller actions should generate. 
This is called behavior driven development.
For example, calling `post /products/create` with a correct product params should `change(Product, :count).by(1)` or `change { ActionMailer::Base.deliveries.count  }.by(1)`

We encourage new coders to test for rendering and redirecting of a controller action.
This is to encourage them to get use to testing controllers.

We highly recommend testing success and failure scenarios for controller actions where creating or updating of database record happens.

## Sample Controller Code

```ruby
# routes
resources :topics, only: [] do
  resources :opinions, only: [:new, :create]
end
# => get /topics/:topic_id/opinions/new
# => post /topics/:topic_id/opinions/create

# controller
class OpinionsController < ApplicationController
  include TopicsTracker
  before_action :redirect_if_topic_is_completed, only: :new

  def new
    @opinion = current_topic.opinions.new    
  end

  def create    
    @opinion = current_topic.opinions.build(opinion_params)

    if @opinion.save
      mark_topic_as_completed(topic_id)
      redirect_to_next_topic
    else
      render :new
    end
  end

  private

  def opinion_params
    params.require(:opinion)
          .permit(:content, :agree)
  end

  def topic_id
    params[:topic_id]
  end

  def current_topic
    @current_topic ||= topic_id.present? ? Topic.find(topic_id) : Topic.first
  end

  def redirect_if_topic_is_completed
    redirect_to_next_topic if completed_topics.include? current_topic.id
  end

  def redirect_to_next_topic
    next_topic = Topic.next_incompleted_topic(completed_topics)    

    if next_topic
      redirect_to new_topic_opinion_url(topic_id: next_topic.id)
    else
      redirect_to thank_you_opinions_url
    end
  end
end
```
