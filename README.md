# TallerConstruccion
public class PesoValor {

    public static void modificarValor(double numero) {
        numero = 500.0;

        System.out.println(
                "Valor dentro del metodo: " + numero
        );
    }

    public static void main(String[] args) {

        double valor = 100.0;

        System.out.println(
                "Valor antes del metodo: " + valor
        );

        modificarValor(valor);

        System.out.println(
                "Valor despues del metodo: " + valor
        );
    }
}


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

    public Paquete(String codigo, String destino) {
        this(codigo, destino, 1.0, false);
    }

    public Paquete(String codigo) {
        this(codigo, "Por asignar");
    }

    public void mostrarInformacion() {
        System.out.println(
            codigo + " -> " + destino
            + " | " + peso + " kg"
            + " | asegurado: " + asegurado
        );
    }

    public void mostrarInformacion(String encabezado) {
        System.out.println(encabezado);
        mostrarInformacion();
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
}


public class Hotel {

    public static void main(String[] args) {

        Habitacion h1 = new Habitacion(
                101,
                "Sencilla"
        );

        Habitacion h2 = new Habitacion(
                102,
                "Doble",
                180000,
                false
        );

        Habitacion h3 = new Habitacion(
                103,
                "Suite"
        );

        h2.ocupar();

        System.out.println(
                "HABITACIONES DEL HOTEL"
        );

        h1.mostrarInformacion();
        h2.mostrarInformacion();
        h3.mostrarInformacion();

        System.out.println();

        System.out.println(
                "DISPONIBILIDAD"
        );

        System.out.println(
                "Habitacion 101 disponible: "
                + h1.estaDisponible()
        );

        System.out.println(
                "Habitacion 102 disponible: "
                + h2.estaDisponible()
        );

        System.out.println(
                "Habitacion 103 disponible: "
                + h3.estaDisponible()
        );

        System.out.println();

        System.out.println(
                "CALCULO DE ESTADIA"
        );

        double estadiaNormal =
                h1.calcularEstadia(3);

        double estadiaDescuento =
                h1.calcularEstadia(3, 10);

        System.out.println(
                "3 noches sin descuento: "
                + estadiaNormal
        );

        System.out.println(
                "3 noches con 10% de descuento: "
                + estadiaDescuento
        );
    }
}


public class Habitacion {

    int numero;
    String tipo;
    double precioNoche;
    boolean ocupada;

     public Habitacion(
            int numero,
            String tipo,
            double precioNoche,
            boolean ocupada) {

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

    public double calcularEstadia(
            int noches,
            double descuento) {

        double valorNormal = calcularEstadia(noches);

        double valorDescuento =
                valorNormal * descuento / 100;

        return valorNormal - valorDescuento;
    }

    public void mostrarInformacion() {
        System.out.println(
                "Habitacion " + numero
                + " | Tipo: " + tipo
                + " | Precio por noche: $" + precioNoche
                + " | Ocupada: " + ocupada
                + " | Disponible: " + estaDisponible()
        );
    }
}


public class Envios {

    public static void main(String[] args) {

        Paquete p1 = new Paquete(
                "P-001",
                "Manizales",
                3.0,
                true
        );

        Paquete p2 = new Paquete(
                "P-002",
                "Pereira"
        );

        Paquete p3 = new Paquete(
                "P-003"
        );

        System.out.println("INFORMACION INICIAL");

        p1.mostrarInformacion();
        p2.mostrarInformacion();
        p3.mostrarInformacion();

        System.out.println();

        p3.actualizarPeso(2.5);

        System.out.println("DESPUES DE ACTUALIZAR P3 ");
        p3.mostrarInformacion();

        System.out.println();

        double costoP1 = p1.calcularCosto();
        double costoP2 = p2.calcularCosto();
        double costoP3 = p3.calcularCosto();

        System.out.println("Costo p1: " + costoP1);
        System.out.println("Costo p2: " + costoP2);
        System.out.println("Costo p3: " + costoP3);

        double total = costoP1 + costoP2 + costoP3;

        System.out.println("Total del envio: " + total);

        System.out.println();

        System.out.println("TARIFA PERSONALIZADA ");
        System.out.println("p1 con tarifa de 4000: "
                + p1.calcularCosto(4000));

        System.out.println("p2 con tarifa de 4000: "
                + p2.calcularCosto(4000));

        System.out.println();

        p1.mostrarInformacion("DATOS DEL PAQUETE P1");

        System.out.println();

        System.out.println(" REVISION DE PESO ");

        if (p1.esPesado()) {
            System.out.println(
                    "P1 requiere manejo especial."
            );
        } else {
            System.out.println(
                    "P1 no requiere manejo especial."
            );
        }

        if (p2.esPesado()) {
            System.out.println(
                    "P2 requiere manejo especial."
            );
        } else {
            System.out.println(
                    "P2 no requiere manejo especial."
            );
        }

        if (p3.esPesado()) {
            System.out.println(
                    "P3 requiere manejo especial."
            );
        } else {
            System.out.println(
                    "P3 no requiere manejo especial."
            );
        }
    }
}
1. ¿Por qué aparecen null, 0.0 y false?
Porque cuando no damos valores a los atributos, Java les pone automáticamente unos valores iniciales: null para textos, 0.0 para double y false para boolean.
2. ¿Por qué new Paquete() dejó de funcionar?
Porque al crear un constructor con parámetros, Java deja de crear automáticamente el constructor vacío. Si todavía queremos crear paquetes sin datos, debemos crear nosotros mismos un constructor sin parámetros.
3. ¿Qué pasa con peso = peso;?
El programa compila, pero realmente no cambia el atributo. Esa instrucción termina asignando el parámetro a sí mismo. Para cambiar el atributo correctamente se usa this.peso = peso.
4. ¿Qué versión de calcularCosto se ejecuta?
Sin parámetros se usa el método normal. Con 4000 se usa el método que recibe una tarifa. Con "4000" no funciona porque ese dato es texto y no existe un método que reciba un String. 
5. ¿Cuáles constructores de Habitacion pueden existir?
Los dos que reciben un int y un String en ese orden no pueden estar juntos, aunque tengan nombres de parámetros diferentes, porque para Java tienen la misma firma. El que recibe primero String y después int sí puede existir, porque el orden cambia. El que recibe solamente un int también puede existir.
6. ¿Qué hace esPesado()?
Sirve para saber si un paquete pesa más de 5 kilos. Si supera ese peso, se considera pesado y puede recibir un aviso de manejo especial. 
7. ¿Para qué sirve mostrarInformacion(String encabezado)?
Sirve para mostrar un título antes de los datos del paquete y después reutilizar el método que ya muestra la información. Así no tenemos que repetir código. 
8. ¿Qué es el paso por valor?
Significa que al pasar un número a un método, se manda una copia del valor. Si el método cambia esa copia, la variable original no cambia. 
Preguntas de comprensión
9. ¿Cuál es la diferencia entre un constructor y un método?
El constructor sirve para preparar un objeto cuando se crea. Un método sirve para realizar alguna acción después. El constructor tiene el mismo nombre de la clase y no tiene tipo de retorno, mientras que un método puede tener otro nombre y devolver un valor. 
10. ¿Por qué new Paquete() dejó de compilar?
Porque al crear un constructor con parámetros, Java ya no crea automáticamente uno vacío. Si queremos seguir creando paquetes sin información, debemos crear manualmente un constructor sin parámetros. 
11. ¿Qué es la firma de un método?
Es la forma que usa Java para diferenciar métodos: tiene en cuenta el nombre, la cantidad, el tipo y el orden de los parámetros. El tipo de retorno no cuenta para diferenciar métodos. 
12. ¿Qué ventaja tiene usar this(...)?
Permite reutilizar otro constructor en vez de escribir nuevamente toda la inicialización. Así se repite menos código, es más fácil de mantener y se reducen errores
