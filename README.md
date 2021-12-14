# CSS-Learning-Track
Collections of notes/resources/examples for my learning on CSS

## FlexBox
### Notes
FlexBox was designed as a one-dimensional layout model means flexbox deals with the layout in one direction at a time either as a row only or as a column only.

`1. display: flex;`
- To define element as a flex container. It enables a flex context for all its direct children.

`2. flex-direction`
- When we're working with flex, there is two axis. main-axis and cross-axis which is perpendicular to main-axis.
- Now we can define main-axis via flex-direction property.
- flex-direction: row | row-reverse | column | column-reverse;
- In row or row-reverse, your main axis will run along the row in the inline direction. In column or column-reverse, your main axis will run from the top of the page to the bottom — in the block direction. And Cross-axis will be always perpendicular to main axis
- For more understanding see [this](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox#the_main_axis)

`3. justify-content & align-items`
- Justify content define alignment of flex items along the main-axis while align-items define alignment of flex-items along the cross-axis.

`4. flex-wrap`
- By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with this property.

`5. order`
- This property will be used on flex-item to controls the order in which they appear in the flex container.

`6. flex-grow`
- This property specifies how much of the remaining space in the flex container should be assigned to the item (the flex grow factor).
- If all sibling items have the same flex grow factor, then all items will receive the same share of remaining space, otherwise it is distributed according to the ratio defined by the different flex grow factors
- For Example see [this](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow#setting_flex_item_grow_factor)

`7. flex-shrink`
- This property specifies how much the item will shrink relative to the rest of the flexible items inside the flex container.
-  If the size of all flex items is larger than the flex container, items shrink to fit according to flex-shrink
- For Example see FlexBox > Basic Properties > [Example 2](https://github.com/utsavpatel51/CSS-Learning-Track/tree/main/FlexBox/Basic%20Properties). More understanding [here](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink#setting_flex_item_shrink_factor)

`8. flex-basis`
- This property specifies the initial/default length of a flexible item.
- when the flex-basis of the first item is 200px, it will start out at 200px but then shrink to fit the space available with the other items being at least min-content sized.
- `flex` is shorthand for 'flex-grow, flex-shrink, flex-basis'.

### Resources
- https://css-tricks.com/snippets/css/a-guide-to-flexbox/
- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout
- https://css-tricks.com/understanding-flex-grow-flex-shrink-and-flex-basis/


## Grid
### Notes
CSS Grid Layout is a two-dimensional grid-based layout system. 

Flexbox is also a very great layout tool, but its for one-directional flow. While flexbox can make rows and columns in the sense that it allows elements to wrap, there’s no way to declaratively control where elements end up since the elements merely push along a single axis and then wrap or not wrap accordingly.

While Grid can be used as "two dimensional". we can declare the sizing of rows and columns and then explicitly place things into both rows and columns as we choose.

`1. display: grid`
- To define element as grid container for its content.

`2. grid-template-columns & grid-template-rows`

- Defines the columns and rows of the grid with a space-separated list of values. Value can be length, percentage, or fr (fraction of the free space in grid)
- This will create grid with 4 columns and 3 rows.
    ```css
    grid-template-columns: 1fr 1fr 1fr 1fr;
    /* each item to take one forth width of grid container */
    grid-template-rows: 20% 1fr 1fr;
    /* we can also specify auto to figure out automatically based on content */
    ```
- If values have repetitive part we can use `grid-template-columns: repeat(4, 1fr)` instead repeating same value again and again.
- For more see Grid > Basic Properties > [Example 1](https://github.com/utsavpatel51/CSS-Learning-Track/tree/main/Grid/Basic%20Properties)

We have created grid template. Now what about positioning the element inside grid?

`3. grid-template-areas`

- Define the grid templated by using the name of the grid provided to individual grid-item using `grid-area: header1`.

- This will create a grid that’s four columns wide by three rows tall. Entire top bar would be cover by header. In the middle two column will be cover by main, one will remain empty and last will be cover by sidebar. Last row is all footer same as header.
    ```css
    .item-a {
        grid-area: header;
    }
    .item-b {
        grid-area: main;
    }
    .item-c {
        grid-area: sidebar;
    }
    .item-d {
        grid-area: footer;
    }

    .container {
        display: grid;
        grid-template-columns: 50px 50px 50px 50px;
        grid-template-rows: auto;
        grid-template-areas: 
            "header header header header"
            "main main . sidebar"
            "footer footer footer footer";
    }
    ```

`4. grid-template`
- Shorthand property for `grid-template-area`, `grid-template-columns` and `grid-template-row`.

`5. column-gap & row-gap`

- To provide the gap between grid-line. We can also use `gap` as shorthand for `row-gap` and `column-gap`.

`6. justify-items & align-items`

- justify-items aligns grid items along the *inline (row)* axis when align-items aligns along block (column) axis. This property aligns the grid-item inside grid and not the whole grid itself
- Sometime a grid might have small size compare to it's grid-container so to align whole grid-container use `justify-content` and `align-content`.

`7. grid-column and grid-row`

- Its also use for grid placement so we can use this in place of grid-template-areas.
    
    ```css
    .item {
      grid-column: <start-line>(grid-column-start) / <end-line>(grid-column-end) OR <start-line> / span <value>;
      grid-row: <start-line>(grid-row-start) / <end-line>(grid-row-end) OR <start-line> / span <value>;
    }
    ```
    For more see Grid > Basic Properties > [Example 2a & 2b](https://github.com/utsavpatel51/CSS-Learning-Track/tree/main/Grid/Basic%20Properties).
- To see use-case difference between grid-template-area and grid-column/grid-row see Grid > Basic Properties > [Example 3a & 3b](https://github.com/utsavpatel51/CSS-Learning-Track/tree/main/Grid/Basic%20Properties).

`8. grid-auto-rows & grid-auto-columns`

- If a grid item is positioned into a row that is not explicitly sized by grid-template-rows, implicit grid tracks are created to hold it and to specify the size for that implicit grid use this both properties.
- For more understanding see [this](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row).

### Resources
- https://css-tricks.com/snippets/css/complete-guide-grid/
- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout
- https://css-tricks.com/quick-whats-the-difference-between-flexbox-and-grid/
- https://www.youtube.com/watch?v=705XCEruZFs