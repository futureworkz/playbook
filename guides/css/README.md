# CSS Development Methodology

## Objective
- Easy to read and change
- Fast to code

## BEM (Block - Element - Modifier)
Each block corresponds to a partial  
File: `/assets/stylesheets/products/_product.scss` -> `/views/products/_product.slim`  
File: `/assets/stylesheets/shared/menu.scss` -> `/views/shared/menu.slim`  

A block is re-usable and always expand to 100%  
Block should not have margin but uses padding for internal elements  
Elements containing sub-blocks will set the width/height of the sub-blocks and should never style the sub-blocks  

### Page BEM
Page block is a block that hold (namespace) the whole page. 
Elements are mostly just holding sub-blocks so CSS is only positioning and sizing.  
Any modifiers are usually just positioning or layouts changes.  
File: /assets/stylesheets/products/index.scss -> /views/products/index.slim

### Mobile responsive
Each block implements its own response to screen sizes.  
Parent blocks will implement the sizes of the sub-blocks in response to screen sizes.  

### Other files
- `/assets/stylesheets/_variables.scss`
- `/assets/stylesheets/_mixins.scss`
- `/assets/stylesheets/global.scss`
- `/assets/stylesheets/fonts.scss`

## Rules:
- A block is always re-usable in any screen resolutions so all CSS rules are within the block file itself
- Block don't position itself and is always 100% width but block positions its elements using padding
- Elements can position itself because they are not re-usable
- It does not matter greatly if a CSS rule is in element or modifier when it is not clear (as long as the code is in the block file itself)
- A parent block NEVER style a containing block: create a modifier for the containing block and use it
