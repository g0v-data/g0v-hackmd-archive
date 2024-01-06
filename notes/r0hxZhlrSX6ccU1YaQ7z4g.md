# Week 12 - Graphs

## Team

>Members:
>
>- Margarita Konnari, 527941
>- Jiangshan Liu, 539663
>
> Date: *day* *month* 2023                                                        |      |

## Activities

Make sure to have the activities signed off regularly to ensure progress is tracked.

Download the provided project and open it in CLion. **NOTE**: in this week you will have to reuse the code of last week. Follow the instructions given in the `main.cpp` file.

### Activity 1: Applications of graphs

1. Social Networks (Undirected Graph):

What does the graph represent? 
Social connections between individuals or entities.
What do the vertices and edges represent? 
Vertices represent individuals or entities, and edges represent relationships or connections between them.
Are the edges directed or undirected? 
Undirected, as social connections are typically bidirectional.

2. Road Networks (Undirected Graph):

What does the graph represent? 
Connections between different road segments or intersections in a network of roads.
What do the vertices and edges represent? 
Vertices represent road segments or intersections, and edges represent the connections or links between them.
Are the edges directed or undirected? 
Undirected, as the connections between road segments are typically bidirectional.

3. Chemical Molecules (Undirected Graph):

What does the graph represent? Structural relationships between atoms in a chemical molecule.
What do the vertices and edges represent? Vertices represent atoms, and edges represent chemical bonds between the atoms.
Are the edges directed or undirected? Undirected, as chemical bonds are typically bidirectional.

4. Internet Web Pages (Directed Graph):

What does the graph represent? 
Web pages on the internet and the hyperlinks between them.
What do the vertices and edges represent? 
Vertices represent web pages, and edges represent hyperlinks from one page to another.
Are the edges directed or undirected? 
Directed, as hyperlinks typically point from one page to another, creating a directed relationship.

5. Flight Routes (Directed Graph):

What does the graph represent? 
Routes between different airports and destinations in an airline network.
What do the vertices and edges represent? 
Vertices represent airports or destinations, and edges represent the flight routes between them.
Are the edges directed or undirected? 
Directed, as flights have specific directions and may not be bidirectional.

6. Dependency Relationships in Software (Directed Graph):

What does the graph represent? 
Dependencies between different modules, components, or libraries in a software system.
What do the vertices and edges represent? 
Vertices represent modules, components, or libraries, and edges represent dependencies between them.
Are the edges directed or undirected? 
Directed, as dependencies indicate a one-way relationship between software components.

### Activity 2: Visualizing graphs

```cpp
// First graph
data::graph g{false}; // create an undirected graph
g.add_edge("a", "c");
g.add_edge("c", "b");
g.add_edge("c", "d");
g.add_edge("b", "d");
g.add_edge("d", "e");
g.add_edge("c", "f");
g.add_edge("f", "g");
dot_writer::write(g, "first.dot");
```

```cpp
// Second graph
data::graph g{true}; // create a directed graph
g.add_edge("a", "b");
g.add_edge("b", "d");
g.add_edge("d", "c");
g.add_edge("c", "a");
g.add_edge("d", "e");
g.add_edge("e", "f");
g.add_edge("f", "g");
g.add_edge("g", "e");
g.find_edge("b", "d").set_colour(data::colour::red);
g.find_edge("d", "e").set_colour(data::colour::red);
g.find_edge("e", "f").set_colour(data::colour::red);
dot_writer::write(g, "second.dot");
```

### Activity 3: Finding a path

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
    // TODO:
    //  Make sure that the correct result is returned (Activity 3)
    
    if (start_vertex == goal)
        return true;
        
    auto &vertex = m_graph[start_vertex]; // get (reference to) vertex ref from name
    for(const auto& edge : vertex.edges()) { // go over the outgoing edges of the vertex
        auto &target_vertex = edge.target();
        
        if(find_path(target_vertex.name(), goal)){
            return true; // found
        }
    }
    return false; // no path found
}

```

### Activity 4: Keeping track of the path

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
    // TODO:
    //  Colour the path (Activity 4)
    
    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); // add start_vertex to m_path
    
    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true;
    }
    
    auto &vertex = m_graph[start_vertex]; // get (reference to) vertex ref from name
    for(const auto& edge : vertex.edges()) { // go over the outgoing edges of the vertex
        auto &target_vertex = edge.target();
        
        if(find_path(target_vertex.name(), goal)){
        
        // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
            m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
            vertex.set_colour(data::colour::red);
            return true; // found
        }
    }
    m_path.pop_back(); // remove start_vertex from m_path
    return false; // no path found
}
```

### Activity 5: Keeping track of visited vertices

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
     // TODO:
    //  Make sure that no vertices are visited twice (Activity 5)
    
    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); // add start_vertex to m_path
    
    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true; // found
    }
    
    auto &vertex = m_graph[start_vertex]; // get (reference to) vertex ref from name
    for(const auto& edge : vertex.edges()) { // go over the outgoing edges of the vertex
        auto &target_vertex = edge.target();
        auto found = std::find(m_path.begin(), m_path.end(), target_vertex.name()); // search for target_vertex.name() in the m_path
        
        if((found == m_path.end()) && (find_path(target_vertex.name(), goal)){ // not found so target vertex becomes the new starting vertex

        // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
            m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
            vertex.set_colour(data::colour::red);
            
            return true; // found
        }
    }
    m_path.pop_back(); // remove start_vertex from m_path
    return false; // no path found
}
```
### Activity 6: Detecting cycles

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
    // TODO:
    //  Keep track of number of visits to avoid cycles (Activity 6)

    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); // add start_vertex to m_path

    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true; // found
    }

    auto &vertex = m_graph[start_vertex]; // get (reference to) vertex ref from name
    for(const auto& edge : vertex.edges()) { // go over the outgoing edges of the vertex
        auto &target_vertex = edge.target();
        auto found = std::find(m_path.begin(), m_path.end(), target_vertex.name()); // search for target_vertex.name() in the m_path

        if((found == m_path.end())) {
            if (find_path(target_vertex.name(), goal)) { // not found so target vertex becomes the new starting vertex

                // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
                m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
                vertex.set_colour(data::colour::red);

                return true; // found
            }
        }
        else{
            m_cycle_found = true; // a cycle has been found
        }
    }
    m_path.pop_back(); // remove start_vertex from m_path
    return false; // no path found
}
```

### Activity 7: Colouring cycles

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
    // TODO:
    //  Colour the cycle (Activity 7)

    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); // add start_vertex to m_path

    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true; // found
    }

    auto &vertex = m_graph[start_vertex]; // get (reference to) vertex ref from name
    for(const auto& edge : vertex.edges()) { // go over the outgoing edges of the vertex
        auto &target_vertex = edge.target();
        auto found = std::find(m_path.begin(), m_path.end(), target_vertex.name()); // search for target_vertex.name() in the m_path

        if((found == m_path.end())) {
            if (find_path(target_vertex.name(), goal)) { // not found so target vertex becomes the new starting vertex

                // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
                m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
                vertex.set_colour(data::colour::red);

                return true; // found
            }
        }
        else{
            if(!m_cycle_found){
                m_cycle_found = true; // a cycle has been found
                m_graph[start_vertex].set_colour(data::colour::blue);
                m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::blue);
                for (auto it = found; it != m_path.end(); it++) { 
                    m_graph[*it].set_colour(data::colour::blue); // color all the vertices
                    if (std::next(it) != m_path.end()) {
                        m_graph.find_edge(*it, *std::next(it)).set_colour(data::colour::blue); // and edges of the cycle
                    }
                }
            }

        }
    }
    m_path.pop_back(); // remove start_vertex from m_path
    return false; // no path found
}
```

### Activity 8: Keeping track of post order

```cpp
void topological_sort::dfs(const std::string& vertex) {
        // TODO: Implement DFS, when a vertex is post-visited, store it
        //  in the vector m_vertices. (Activity 8)

        m_visited[vertex] = 1; // current vertex visited
        auto& current_vertex = m_graph[vertex]; // get (reference to) vertex ref from name

        for (auto& edge : current_vertex.edges()) { // go over the outgoing edges of the current vertex
            // if the target vertex of the current edge has not been visited yet
            if(m_visited[edge.target().name()] == 0){
                dfs(edge.target().name()); // depth-first search on the target vertex of the current edge
                continue;
            }
            // if the target vertex of the current edge has been visited
            if(m_visited[edge.target().name()] == 1){
                m_cycle_found = true; // cycle has been detected 
                continue;
            }
        }
        m_vertices.push_back(vertex); // post - visited, add current vertex to m_vertices
        m_visited[vertex]++;
    }
```

### Activity 9: Toplogical sorting

```cpp
bool topological_sort::compute() {
        // TODO (Activity 9):
        //  Run DFS on all unvisited vertices in the graph,
        //  keeping track of the post-order of the vertices.
        //  If a cycle is found, return false.
        //  Otherwise, reverse the post order and return true.

        for (auto& vertex : m_graph.vertices()) { // go over each vertex in the graph
            if(m_visited[vertex.name()] == 0){ // current vertex has not been visited yet
                dfs(vertex.name());
            }
        }
        std::reverse(m_vertices.begin(), m_vertices.end());

        return !m_cycle_found; // if cycle found during dfs.. return false
    }
```

### Activity 10: Project scheduling
directed
Concept_Art Game_Design
Game_Design Asset_Creation
Game_Design Level_Design
Game_Design Programming
Asset_Creation Programming
Game_Design Sound_Design
Game_Design User_Interface_Design
Programming Quality_Assurance
Concept_Art Marketing
Game_Design Marketing
Quality_Assurance Release
Marketing Release

```cpp
data::graph graph = data::graph::load("tasks.txt");
algos::topological_sort sort(graph);
sort.compute();
dot_writer::write(graph, "HELP.dot");
```