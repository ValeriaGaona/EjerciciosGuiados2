### Valeria García Gaona - GTID141

#  Tabla de Contenidos

| Documento | Tipo | Descripción | Ver PDF |
|-----------|------|-------------|---------|
| *Lista enlazada con VisuAlgo* | 📄 PDF | Ejercicios de listas enlazadas | [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/VisuAlgo-VGG.pdf) |
| *Curso Listas Java* | 📄 PDF | Curso completo sobre listas en Java | [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/ActividadPreguntasListas-VGG.pdf)|
| *Actividad en clase: listas, listas dobles Java* | 📄 PDF | Actividades prácticas de listas | [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/U2ACT3_Pr%C3%A1ctica_Manual_y_Algor%C3%ADtmica_Lista.pdf) |
| *Actividad en clase: Ejercicio de Pila con VisuAlgo* | 📄 PDF | Ejercicio de Pila con VisuAlgo| [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/U2ACT2_EjercicioDePilaConVisuAlgo.pdf) |
| *Actividad en clase: Colas* | 📄 PDF | Ejercicio de Colas NearPool| [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/Colas-NearPool.pdf)  [Ver Códigos](https://github.com/ValeriaGaona/EjerciciosGuiados2?tab=readme-ov-file#actividad-en-clase-codigo-colas) |

#

## Actividad Lista Encantada Humana 

| Imagen 1 | Imagen 2 | Imagen 3 |
|-----------|-----------|-----------|
| <img src="https://github.com/user-attachments/assets/a092f89b-a822-4499-91f0-0ef8d31ae16a" width="200"> | <img src="https://github.com/user-attachments/assets/ed94720f-23f0-4c21-a8eb-8ab748a86f80" width="200"> | <img src="https://github.com/user-attachments/assets/e11b4929-2bee-4dc5-9cbf-6e0864d2cb94" width="200"> |



#

# Codigo de ejercicio en clase: Pilas

```
/**
 *  Actividad practica en clase Pilas
 * @author Valeria García Gaona - GTID141 - 1224100671 - Fecha 17/10/25 - 1224100671.vgg@gmail.com
 */
public interface IStack <T>{
    void push (T element);
    T pop(); //o void pop();
    T peek();
    boolean isEmpty();
    
}
```


```
package Pilas;

/**
 *  Actividad practica en clase Pilas
 * @author Valeria García Gaona - GTID141 - 1224100671 - Fecha 17/10/25 - 1224100671.vgg@gmail.com
 */
public class StackArray<T> implements IStack<T> {
    
    //definimos los atributos
    private T [] elements; //almacena los elementos
    private int top; ////el indice de la poscicion actual de ultumo elemento

    //costructores
    
    public StackArray(T[] elements, int pop) {
        elements = (T[])new Object[30]; //se le da el tamaño maximo a la pila
    }

    public StackArray(int size) {
        elements = (T[])new Object[size];
    }
    
    @Override
    public void push(T element) {
        
        if(top<elements.length-1){
            top++;
            elements[top] = element; //si no esta llena se inserta un nuevo elemento
        } else {
            System.out.println("Esta llena"); //si esta llena se muestra el mensaje
        }
        
    }

    @Override
    public T pop() {
        
        if (isEmpty()) {
            //si la pila esta vacia no se elimina nada
            System.out.println("Pila Vacia");
            return null;
        } else {
            //elimina y muestra el ultimo elemento eliminado
            T element = elements[top];
            elements[top] = null;
            top--;
            System.out.println("El nombre eliminado es: ");
            return element;
        }
        
    }

    @Override
    public T peek() {
        //si esta vacia simple,emte muestra el mensaje
        if(isEmpty()) {
            System.out.println("Pila Vacía");
        }
        //muestra el ultimo elemento insertado de la pila sin modificarlo
        System.out.println("Conociendo el ultimo de la pila");
        return (T) elements[top]; //[top -1]
         
    }

    @Override
    public boolean isEmpty() {
        //verifica si la pila esta vacia
       return top==0;
    }
    
    public void printStack() {
        //muestra los elemnetos de la pila, desde el primero hasta el ultimo
        System.out.println("Elementos de la pila:");
        for (int i = top; i >= 0; i--) {
            System.out.println(elements[i]);
        }
    }
}
```


```
package Pilas;

/**
 *  Actividad practica en clase Pilas
 * @author Valeria García Gaona - GTID141 - 1224100671 - Fecha 17/10/25 - 1224100671.vgg@gmail.com
 */
public class Main {
    public static void main(String[] args) {
        //se crea la pila donde se almacenaran los nombres
        StackArray<String> nombres = new StackArray<>(30); 
        
        //se insertan los nombres a la pila
        nombres.push("Mabe");
        nombres.push("Sarita");
        nombres.push("Alo");
        nombres.push("Vale");
        
        //se elimina el ultimo insertado
        System.out.println(nombres.pop());
        //se muestra el ultimo elemento insertado
        System.out.println(nombres.peek());
        
        //se inserta un nuevo nombre
        nombres.push("Fer");
        
        //se muestra el ultimo elemento insertado
        System.out.println(nombres.peek());
        //se muestran todos los nombres de la pila en orden
        nombres.printStack();
    }
}
```
#
#
## Actividad en clase: Codigo colas

```
package colas;
import java.util.Scanner;
/**
 *  Actividad: Colas
 * @author Valeria García Gaona - GTID141 - 1224100671 - Fecha 24/10/25 - 1224100671.vgg@gmail.com
 */
public class ColaMain{
    public static void main(String[] args) {
        Cola<String> colaTareas = new Cola<>();
        Scanner scanner = new Scanner(System.in);
        int opcion;

        do {
            System.out.println("\n MENU DE OPERACIONES ");
            System.out.println("1. Agregar tarea");
            System.out.println("2. Mostrar tamaño de la cola");
            System.out.println("3. Consultar frente");
            System.out.println("4. Ejecutar tarea (quitar)");
            System.out.println("5. Mostrar estado final de la cola");
            System.out.println("0. Salir");
            System.out.print("Selecciona una opcion: ");
            opcion = scanner.nextInt();
            scanner.nextLine(); //Espera enter para seguir
            

            switch (opcion) {
                case 1:
                    System.out.print("Ingresa la tarea: ");
                    String tarea = scanner.nextLine();
                    colaTareas.insertar(tarea);
                    scanner.nextLine();
                    break;
                case 2:
                    System.out.println("Tamaño actual: " + colaTareas.getTamaño());
                    scanner.nextLine();
                    break;
                case 3:
                    if (!colaTareas.colaVacia()) {
                        System.out.println("Frente: " + colaTareas.frente());
                    }
                    scanner.nextLine();
                    break;
                case 4:
                    String tareaQuitada = colaTareas.quitar();
                    if (tareaQuitada != null) {
                        System.out.println("Tarea ejecutada: " + tareaQuitada);
                    }
                    scanner.nextLine();
                    break;
                case 5:
                    mostrarEstadoFinal(colaTareas);
                    scanner.nextLine();
                    break;
                case 0:
                    System.out.println("Saliendo del programa...");
                    break;
                default:
                    System.out.println("Opcion invalida.");
            }
        } while (opcion != 0);
    }

    // Método auxiliar para mostrar el estado final
    public static void mostrarEstadoFinal(Cola<String> cola) {
        Nodo<String> actual = cola.getCabeza();
        System.out.println("Estado final de la cola:");
        while (actual != null) {
            System.out.println("- " + actual.getDato());
            actual = actual.getSiguiente();
        }
        System.out.println("Tamaño: " + cola.getTamaño());
    }
}
```

```
package colas;
/**
 *  Actividad: Colas
 * @author Valeria García Gaona - GTID141 - 1224100671 - Fecha 24/10/25 - 1224100671.vgg@gmail.com
 */
public class Nodo<T> {
    private T dato;
    private Nodo siguiente;
    
    public Nodo(T data){
        dato=data;
        siguiente=null;
    }

    public T getDato() {
        return dato;
    }

    public void setDato(T dato) {
        this.dato = dato;
    }

    public Nodo getSiguiente() {
        return siguiente;
    }

    public void setSiguiente(Nodo siguiente) {
        this.siguiente = siguiente;
    }

    @Override
    public String toString() {
        return "Nodo{" + "dato=" + dato + ", siguiente=" + siguiente + '}';
    }
}
```

```
package colas;

/**
 *  Actividad: Colas
 * @author Valeria García Gaona - GTID141 - 1224100671 - Fecha 24/10/25 - 1224100671.vgg@gmail.com
 */
public class Cola <T>{
    private Nodo<T> cabeza;
    private Nodo<T>cola;
    private int tamaño;

    public Cola() {
        this.cabeza = null;
        this.cola = null;
        this.tamaño = 0;
    }
    
    public Nodo<T> getCabeza() {
        return cabeza;
    }

    public void setCabeza(Nodo<T> cabeza) {
        this.cabeza = cabeza;
    }

    public Nodo<T> getCola() {
        return cola;
    }

    public void setCola(Nodo<T> cola) {
        this.cola = cola;
    }

    public int getTamaño() {
        return tamaño;
    }

    public void setTamaño(int tamaño) {
        this.tamaño = tamaño;
    }
    
    public boolean colaVacia(){
        return cabeza==null;
    } 
    
    public void insertar(T elemento) {
        Nodo<T> nuevoNodo = new Nodo<>(elemento);

        if (colaVacia()) { // Caso 1: La cola está vacía
            cabeza = nuevoNodo;
            cola = nuevoNodo;
        } else { // Caso 2: La cola NO está vacía
            cola.setSiguiente(nuevoNodo);
            cola = nuevoNodo;
        }

        tamaño++; // Incrementar tamaño
        System.out.println("-> Insertado: " + elemento);
    }

    public T quitar() {
        if (colaVacia()) {
            System.out.println("Error: La cola esta vacia.");
            return null;
        }

        T datoQuitado = cabeza.getDato(); // Guardamos el dato a devolver
        cabeza = cabeza.getSiguiente();   // Avanzamos la cabeza

        if (cabeza == null) { // Si ya no hay elementos, actualizamos cola
            cola = null;
        }

        tamaño--;
        return datoQuitado;
    }

    public T frente(){
        if(colaVacia()){
            System.out.println("Error: la cola esta vacia");
        }
        return this.cabeza.getDato();
    }
}
```
