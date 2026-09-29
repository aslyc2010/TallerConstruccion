public class Paquete {

    String codigo;
    String destino;
    double peso;
    boolean asegurado;

    public Paquete(String codigo, String destino, double peso, boolean asegurado) {
        this.codigo = codigo;
        this.destino = destino;
        this.peso = peso;
        this.asegurado = asegurado;
    }

    public void mostrarInformacion() {
        System.out.println(codigo + " -> " + destino
                + " | " + peso + " kg | asegurado: " + asegurado);
    }

    public Paquete(String codigo, String destino) {
        this(codigo, destino, 1.0, false);
    }

    public Paquete(String codigo) {
        this(codigo, "Por asignar");
    }

    public void actualizarPeso(double peso) {
        this.peso = peso;
    }

    public double calcularCosto() {
        double costo = peso * 5000;

        if (asegurado) {
            costo = costo + 8000;
        }

        return costo;
    }

    public double calcularCosto(double tarifaPorKilo) {
        double costo = peso * tarifaPorKilo;

        if (asegurado) {
            costo = costo + 8000;
        }

        return costo;
    }

    public boolean esPesado() {
        return peso > 5;
    }

    public void mostrarInformacion(String encabezado) {
        System.out.println(encabezado);
        mostrarInformacion();
    }
}


public class Habitacion {

    int numero;
    String tipo;
    double precioNoche;
    boolean ocupada;

    public Habitacion(int numero, String tipo, double precioNoche, boolean ocupada) {
        this.numero = numero;
        this.tipo = tipo;
        this.precioNoche = precioNoche;
        this.ocupada = ocupada;
    }

    public Habitacion(int numero, String tipo) {
        this(numero, tipo, 120000, false);
    }

    public void ocupar() {
        ocupada = true;
    }

    public boolean estaDisponible() {
        return !ocupada;
    }

    public double calcularEstadia(int noches) {
        return precioNoche * noches;
    }

    public double calcularEstadia(int noches, double descuento) {
        double valor = calcularEstadia(noches);
        return valor - (valor * descuento / 100);
    }

    public void mostrarInformacion() {
        System.out.println("Habitación " + numero
                + " | Tipo: " + tipo
                + " | Precio: " + precioNoche
                + " | Ocupada: " + ocupada);
    }
}

public class Hotel {

    public static void main(String[] args) {

        Habitacion h1 = new Habitacion(101, "Sencilla", 100000, false);
        Habitacion h2 = new Habitacion(102, "Doble");
        Habitacion h3 = new Habitacion(103, "Suite");

        h2.ocupar();

        h1.mostrarInformacion();
        h2.mostrarInformacion();
        h3.mostrarInformacion();

        System.out.println("Estadía: " + h2.calcularEstadia(3));
        System.out.println("Estadía con descuento: " + h2.calcularEstadia(3, 10));
    }
}public class Hotel {

    public static void main(String[] args) {

        Habitacion h1 = new Habitacion(101, "Sencilla", 100000, false);
        Habitacion h2 = new Habitacion(102, "Doble");
        Habitacion h3 = new Habitacion(103, "Suite");

        h2.ocupar();

        h1.mostrarInformacion();
        h2.mostrarInformacion();
        h3.mostrarInformacion();

        System.out.println("Estadía: " + h2.calcularEstadia(3));
        System.out.println("Estadía con descuento: " + h2.calcularEstadia(3, 10));
    }
}

public class Envios {

    public static void main(String[] args) {

        Paquete p1 = new Paquete("P-001", "Manizales", 3.0, true);
        p1.mostrarInformacion();

        Paquete p2 = new Paquete("P-002", "Pereira");
        Paquete p3 = new Paquete("P-003");

        p2.mostrarInformacion();
        p3.mostrarInformacion();

        p3.actualizarPeso(2.5);

        double total = p1.calcularCosto()
                + p2.calcularCosto()
                + p3.calcularCosto();

        System.out.println("Total del envío: " + total);

        System.out.println(p1.calcularCosto(4000));
        System.out.println(p2.calcularCosto(4000));

        if (p1.esPesado()) {
            System.out.println("Manejo especial");
        }

        p1.mostrarInformacion("Información del paquete:");
    }
}


1. ¿Por qué aparecen los valores null, 0.0 y false al crear un paquete sin constructor?
Porque Java coloca valores por defecto cuando los atributos no tienen un valor asignado.
2. ¿Por qué new Paquete() dejó de compilar?
Porque al crear un constructor con parámetros, Java deja de crear automáticamente el constructor vacío.
3. ¿Qué versión de calcularCosto() se ejecuta con p1.calcularCosto()?
Se ejecuta la versión que no recibe parámetros.
4. ¿Qué versión de calcularCosto() se ejecuta con p1.calcularCosto(4000)?
Se ejecuta la versión que recibe un double.
5. ¿Por qué p1.calcularCosto("4000") no compila?
Porque no existe una versión del método que reciba un String.
6. ¿Cuáles constructores de Habitacion pueden existir al mismo tiempo?
Habitacion(int, String), Habitacion(String, int) y Habitacion(int) pueden existir juntos. Los dos primeros con int, String no pueden existir juntos porque tienen la misma firma.
7. ¿Qué hace el método esPesado()?
Devuelve true si el paquete pesa más de 5 kilos.
8. ¿Qué hace mostrarInformacion(String encabezado)?
Muestra el encabezado y después muestra la información del paquete.
9. ¿Qué demuestra el paso por valor con double?
Que cambiar el parámetro dentro del método no cambia la variable original.
10. ¿Qué diferencia hay entre un constructor y un método?
El constructor inicializa el objeto y el método realiza una acción. Además, el constructor no tiene tipo de retorno.
11. ¿Qué pasa con peso = peso en vez de this.peso = peso?
Compila, pero el atributo no cambia porque el parámetro se asigna a sí mismo.
12. ¿Qué es la firma de un método?
Es el nombre del método junto con sus parámetros.
13. ¿Por qué el tipo de retorno no sirve para diferenciar métodos sobrecargados?
Porque la sobrecarga se diferencia por los parámetros, no por el tipo de retorno.
14. ¿Qué ventaja tiene usar this(...) en los constructores?
Permite reutilizar otro constructor y evita repetir código.




