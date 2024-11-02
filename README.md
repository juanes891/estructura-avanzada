#include <iostream>
#include <vector>

using namespace std;
//una estructura que representa una ciudad 
struct NodoCiudad {
//nombre del nodo puede ser pair o ciudad
    string nombre;
//vector que contiene los punteros de los vectores
    vector<NodoCiudad*> hijos;
//constructor que señala el nombre del nodo
    NodoCiudad(string nombre) : nombre(nombre) {}
};
// funcion que imprime el arbol de nodos en forma jerarquica
void imprimirArbol(NodoCiudad* nodo, int nivel = 0) {
    if (!nodo) return;// si el nodo  es nulo sale de la funcion con esta return
//imprimir el nombre del nodo 
    for (int i = 0; i < nivel; i++) cout << " ";
    cout << nodo->nombre << endl;//imprimir el nombre del nodo
//imprimir cada uno de los nodos hijos
    for (auto hijo : nodo->hijos) {
        imprimirArbol(hijo, nivel + 1);
    }
}

int main() {
//crear el nodo raiz para representar el pais 
    NodoCiudad* pais = new NodoCiudad("pais");
//crear nodos que representen los estados
    NodoCiudad* estado1 = new NodoCiudad("estado1");
    NodoCiudad* estado2 = new NodoCiudad("estado2");
    
//agregar ciudades en el primer estado  
    estado1->hijos.push_back(new NodoCiudad("Ciudad A"));
    estado1->hijos.push_back(new NodoCiudad("Ciudad B"));
//agregar ciudades en el segundo estado   
    estado2->hijos.push_back(new NodoCiudad("Ciudad C"));
    estado2->hijos.push_back(new NodoCiudad("Ciudad D"));
    estado2->hijos.push_back(new NodoCiudad("Ciudad E"));
//agregar los estados al nodo raiz    
    pais->hijos.push_back(estado1);
    pais->hijos.push_back(estado2);
// imprimir la estructura del arbol    
    imprimirArbol(pais);
    
    return 0;// fin del programa
}

/////////////
#include <iostream>
#include <vector>
using namespace std;

const int NUM_CIUDADES = 5; // Número de ciudades

// Función que imprime la matriz de adyacencia del grafo
void imprimirGrafo(const vector<vector<int>>& grafo) {
    cout << "Matriz de adyacencia:\n";
    for (int i = 0; i < NUM_CIUDADES; ++i) {
        for (int j = 0; j < NUM_CIUDADES; ++j) {
            cout << grafo[i][j] << " "; // Imprime la conexión entre ciudades
        }
        cout << endl; // Salto de línea por cada ciudad
    }
}

int main() {
    // Inicializa el grafo como una matriz de adyacencia
    vector<vector<int>> grafo(NUM_CIUDADES, vector<int>(NUM_CIUDADES, 0));

    // Conexiones entre ciudades
    grafo[0][1] = grafo[1][0] = 1; // Carretera entre Ciudad 0 y Ciudad 1
    grafo[1][2] = grafo[2][1] = 1; // Carretera entre Ciudad 1 y Ciudad 2
    grafo[2][3] = grafo[3][2] = 1; // Carretera entre Ciudad 2 y Ciudad 3
    grafo[3][4] = grafo[4][3] = 1; // Carretera entre Ciudad 3 y Ciudad 4
    grafo[4][5] = grafo[4][4] = 1; // Carretera entre Ciudad 4 y Ciudad 5

    // Imprime la matriz de adyacencia
    imprimirGrafo(grafo);

    return 0; 
}

///////////

#include <iostream>
#include <map>
#include <utility>

using namespace std;

int main() {
//creamos un mapa para almacear distacias entre ciudades
    map<pair<string, string>, int> distancias;

//asignamos distacias entre pares de ciudades
    distancias[{"ciudad A", "ciudad B"}] = 100;//distacia entre ciudad A y ciudad B
    distancias[{"ciudad B", "ciudad C"}] = 150;//distacia entre ciudad B y ciudad C
    distancias[{"ciudad C", "ciudad D"}] = 200;//distacia entre ciudad C y ciudad D
    distancias[{"ciudad E", "ciudad F"}] = 250;//distacia entre ciudad E y ciudad F
    distancias[{"ciudad G", "ciudad H"}] = 300;//distacia entre ciudad G y ciudad H

//imprimimos las distacias entre las ciudades    
    cout << "Distancias entre ciudades:\n";
    for (const auto& par : distancias) { //iteramos sobre el mapa
        //mostramos la distancia entre cada par de ciudad
        cout << par.first.first << " - " << par.first.second << ": "
             << par.second << " KM\n";//formato de salida
    }

    return 0;//fin del programa
}


