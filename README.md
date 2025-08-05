Abstract board games such as [Settlers of Catan](https://en.wikipedia.org/wiki/Catan) use the edge, vertex and hexagon components of a hexagon grid. This java project implements a similar grid system with built-in support for rendering and mouse interaction.

![](/src/main/resources/image20250805180433.png)
## Composite Hexagon Grid Structure

A **CompositeGrid** consists of a grid of **HexagonCells** and **TriangleCells**.

Each **HexagonCell** contains a reference to the \<**H**> hexagon object. As well as some useful references to the objects it shares a relationship with as follows:

- The **HexagonCoordinate**.

- The six **HexagonCells** it shares a neighbour with.

- The \<**V**> vertex object at the hexagon centroid.

- The six \<**V**> vertex objects along the hexagons border

- The six \<**E**> edge objects along the hexagons border.

- The six \<**E**> edge objects around the centroid.
  
Each **TriangleCell** contains a reference to the \<**V**> vertex object. As well as some useful references to the objects it shares a relationship with as follows:

- The **TriangleCoordinate**.

- The six **TriangleCells** it shares a neighbour with.

- The six \<**E**> edge objects around the vertex.

---

## Coordinates
Two coordinate systems (**HexagonCoordinate** and **TriangleCoordinate**) are used for hexagon and triangle space. Conversion between the two can be handled by using the convert() method in each of the respective Coordinate classes.


## Directions
Two direction enums define the orientation of neighbors and edges.

A **HexagonDirection** involves the directions: NORTHWEST, NORTH, NORTHEAST, SOUTHEAST, SOUTH, SOUTHWEST.

A **TriangleDirection** involves the directions: WEST, NORTHWEST, NORTHEAST, EAST, SOUTHEAST, SOUTHWEST

## Generics and Creation
The hexagon, vertex and edge objects are type associated as follows:

- CompositeGrid<H, V, E>
- HexagonCell<H, V, E>
- TriangleCell<V, E>

Grid creation requires the respective (no-arg) Classes as a parameter. The following would create a String object at each hexagon, vertex and edge.

`CompositeGrid<String, String, String> compositeGrid = new CompositeGrid<String, String, String>(100, 100, String.class, String.class, String.class);`

It is recommended to wrap custom grids in a separate class so as to shield users from the added complexity of type associations.

---

**Visualising the grid objects and their coordinate systems:**

![](/src/main/resources/image20250805153639.png)

![](/src/main/resources/image20250805151003.png)

![](/src/main/resources/image20250805150628.png)

![](/src/main/resources/image20250805150705.png)

![](/src/main/resources/image20250805150807.png)

## Rendering
Rendering to a Graphics2D canvas can be achieved by overriding the abstract methods in AbstractGridRenderer. All screen geometry is pre-calculated and presented to the user as parameters in their respective methods.
## Swing
A HexagonGridPane encapsulates the rendering and mouse functionality.  Grid selection (mouse clicks) events can be subscribed to by the addGridSelectionListener() method.
