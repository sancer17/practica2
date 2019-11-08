**Práctica de búsqueda heurística sin adversarios**

1. ¿Qué variable representa la lista ABIERTA?  
Esta lista **ABIERTA** es una estructura de datos auxiliar que contiene una cola de prioridad con los valores f(n) de cada nodo a evaluar.
En este caso la variable que la representa es:

  
	`final List<Graph.Vertex<T>> openSet = new ArrayList<Graph.Vertex<T>>(size)`

2. ¿Qué variable representa la función *g*?  
La función **g(n)** representa el coste real del camino para llegar al nodo n desde el nodo inicial.  
En este caso la variable que la representa es:

	`final Map<Graph.Vertex<T>,Integer> gScore = new HashMap<Graph.Vertex<T>,Integer>()`

3. ¿Qué variable representa la función *f*?  
La función **f(n)** representa el coste total desde el incio hasta el destino pasando por el nodo n. Es la suma del *g(n)* y *h(n)*. La lista *ABIERTA* se ordena en funcion de *f(n)*.    
En este caso la variable que la representa es:  

	`final Map<Graph.Vertex<T>,Integer> fScore = new HashMap<Graph.Vertex<T>,Integer>()` 

4. ¿Qué método habría que modificar para que la heurística representara
la distancia aérea entre vértices?  
El método a modificiar sería el:  
	
	`protected int heuristicCostEstimate(Graph.Vertex<T> start, Graph.Vertex<T> goal)`  

	Porque por defecto está devolviendo un coste heurístico de **1**.

5. ¿Realiza este método reevaluación de nudos cuando se encuentra una
nueva ruta a un determinado vértice? Justifique la respuesta.  
No, porque los nodos ya evaluados se añadaen a la lista de **CERRADOS** y cuandose comprueba que un vértice pertenece a esta lista se pasa por alto.  
Lo podemos apreciar en el siguiente trozo de código:  

~~~

	if (closedSet.contains(neighbor))
                    continue; // Ignore the neighbor which is already evaluated.

~~~
