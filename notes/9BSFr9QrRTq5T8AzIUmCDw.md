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

```cpp=
bool visitor::find_path(const string &start_vertex, const string &goal) {
    // TODO:
    //  Make sure that the correct result is returned (Activity 3)
    if (start_vertex == goal)
        return true;
    auto &vertex = m_graph[start_vertex];
    for(const auto& edge : vertex.edges()) {
        auto &target_vertex = edge.target();
        if(find_path(target_vertex.name(), goal)){
            return true;
        }
    }
    return false;
}

```

### Activity 4: Keeping track of the path

```cpp=
bool visitor::find_path(const string &start_vertex, const string &goal) {
    // TODO:
    //  Colour the path (Activity 4)
    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); //add the start_vertex to the m_path vector
    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true;
    }
    auto &vertex = m_graph[start_vertex];
    for(const auto& edge : vertex.edges()) {
        auto &target_vertex = edge.target();
        // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
        if(find_path(target_vertex.name(), goal)){
            m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
            vertex.set_colour(data::colour::red);
            return true;
        }
    }
    m_path.pop_back();
    return false;
}
```

### Activity 5: Keeping track of visited vertices

```cpp=
bool visitor::find_path(const string &start_vertex, const string &goal) {
    //  Make sure that no vertices are visited twice (Activity 5)
    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); //add the start_vertex to the m_path vector
    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true;
    }
    auto &vertex = m_graph[start_vertex];
    for(const auto& edge : vertex.edges()) {
        auto &target_vertex = edge.target();
        auto found = std::find(m_path.begin(), m_path.end(), target_vertex.name());
        // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
        if(found == m_path.end() && find_path(target_vertex.name(), goal)){
            m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
            vertex.set_colour(data::colour::red);
            return true;
        }
    }
    m_path.pop_back();
    return false;
}
```

### Activity 6: Detecting cycles

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
    //  Keep track of number of visits to avoid cycles (Activity 6)
    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); //add the start_vertex to the m_path vector
    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true;
    }
    auto &vertex = m_graph[start_vertex];
    for(const auto& edge : vertex.edges()) {
        auto &target_vertex = edge.target();
        auto found = std::find(m_path.begin(), m_path.end(), target_vertex.name());
        // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
        if(found == m_path.end()){
            if(find_path(target_vertex.name(), goal)){
                m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
                vertex.set_colour(data::colour::red);
                return true;
            }
        } 
        else{
            m_cycle_found = true;
        }
    }
    m_path.pop_back();
    return false;
}
```

### Activity 7: Colouring cycles

```cpp
bool visitor::find_path(const string &start_vertex, const string &goal) {
    //  Colour the cycle (Activity 7)
    //m_path keeps track of the current path being explored
    m_path.push_back(start_vertex); //add the start_vertex to the m_path vector
    if (start_vertex == goal) {
        m_graph[start_vertex].set_colour(data::colour::red);
        return true;
    }
    auto &vertex = m_graph[start_vertex];
    for(const auto& edge : vertex.edges()) {
        auto &target_vertex = edge.target();
        auto found = std::find(m_path.begin(), m_path.end(), target_vertex.name());
        // sets the colour of the start_vertex and the edge between the start_vertex and the target_vertex to red
        if(found == m_path.end()){
            if(find_path(target_vertex.name(), goal)){
                m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::red);
                vertex.set_colour(data::colour::red);
                return true;
            }
        }
        else{
            if (!m_cycle_found) {
                m_cycle_found = true;
                m_graph[start_vertex].set_colour(data::colour::blue);
                m_graph.find_edge(start_vertex, target_vertex.name()).set_colour(data::colour::blue);
                for (auto it = found; it != m_path.end(); it++) {
                    m_graph[*it].set_colour(data::colour::blue);
                    if (std::next(it) != m_path.end()) {
                        m_graph.find_edge(*it, *std::next(it)).set_colour(data::colour::blue);
                    }
                }
            }
        }
    }
    m_path.pop_back();
    return false;
}
```

### Activity 8: Keeping track of post order

```cpp=
void topological_sort::dfs(const std::string& vertex) {
    m_visited[vertex] = 1;
    auto& current_vertex = m_graph[vertex];
    for (auto& edge : current_vertex.edges()) {
        if(m_visited[edge.target().name()] == 0){
            dfs(edge.target().name());
            continue;
        }
        if(m_visited[edge.target().name()] == 1){
            m_cycle_found = true;
            continue;
        }
    }
    m_vertices.push_back(vertex);
    m_visited[vertex]++;
}
```

### Activity 9: Toplogical sorting

```cpp=
bool topological_sort::compute() {
    for (auto& vertex : m_graph.vertices()) {
        if(m_visited[vertex.name()] == 0){
            dfs(vertex.name());
        }
    }
    std::reverse(m_vertices.begin(), m_vertices.end());

    return !m_cycle_found;
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