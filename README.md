#

##  Tabla de Contenidos

| Documento | Tipo | Descripción | Ver PDF |
|-----------|------|-------------|---------|
| *Lista enlazada con VisuAlgo* | 📄 PDF | Ejercicios de listas enlazadas | [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/VisuAlgo-VGG.pdf) |
| *Curso Listas Java* | 📄 PDF | Curso completo sobre listas en Java | [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/ActividadPreguntasListas-VGG.pdf)|
| *Actividad en clase: listas, listas dobles Java* | 📄 PDF | Actividades prácticas de listas | [Ver PDF](https://github.com/ValeriaGaona/EjerciciosGuiados2/blob/main/U2ACT3_Pr%C3%A1ctica_Manual_y_Algor%C3%ADtmica_Lista.pdf) |

# Actividad Lista Encantada Humana 

| Imagen 1 | Imagen 2 | Imagen 3 |
|-----------|-----------|-----------|
| <img src="https://github.com/user-attachments/assets/a092f89b-a822-4499-91f0-0ef8d31ae16a" width="200"> | <img src="https://github.com/user-attachments/assets/ed94720f-23f0-4c21-a8eb-8ab748a86f80" width="200"> | <img src="https://github.com/user-attachments/assets/e11b4929-2bee-4dc5-9cbf-6e0864d2cb94" width="200"> |





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
