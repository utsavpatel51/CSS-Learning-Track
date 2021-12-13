# CSS-Learning-Track
Collections of notes/resources/examples for my learning on CSS


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

`3. grid-template-areas`:

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

`8. grid-auto-rows & grid-auto-columns`:

- If a grid item is positioned into a row that is not explicitly sized by grid-template-rows, implicit grid tracks are created to hold it and to specify the size for that implicit grid use this both properties.
- For more understanding see [this](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row).

### Resources
- https://css-tricks.com/snippets/css/complete-guide-grid/
- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout
- https://css-tricks.com/quick-whats-the-difference-between-flexbox-and-grid/