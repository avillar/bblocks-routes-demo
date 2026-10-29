# Route

A **route** is a road or path that can be followed from one place to another.

In this model a route is an ordinary OGC *feature* (so it can be shared and mapped like any other), with:

- a **geometry** made of one or more lines (`MultiLineString`), so a route can have several segments;
- a **`length`** in metres (required, greater than zero);
- an optional **`name`**.

See the example for a short route in Valencia, Spain.
