import java.util.List;
import java.util.Random;

class PanelSolarRotativo {
    private String tamaño;
    private String material;
    private boolean esRotativo;

    public PanelSolarRotativo(String tamaño, String material, boolean esRotativo) {
        this.tamaño = tamaño;
        this.material = material;
        this.esRotativo = esRotativo;
    }

    public void generarEnergia() {
        System.out.println("Generando energía solar...");
        
        Random random = new Random();
        double energiaGenerada = random.nextDouble() * 100; /
        System.out.println("Energía generada: " + energiaGenerada + " watts");
    }

    public void rotar() {
        System.out.println("Rotando el panel solar...");
     
        System.out.println("El panel solar está rotando automáticamente.");
    }
}


class Arduino {
    private String modelo;
    private List<String> conexiones;

    public Arduino(String modelo, List<String> conexiones) {
        this.modelo = modelo;
        this.conexiones = conexiones;
    }

    public String getModelo() {
        return modelo;
    }

    public List<String> getConexiones() {
        return conexiones;
    }

    public void leerEntradas() {
        System.out.println("Leyendo entradas desde Arduino...");
       
        for (String conexion : conexiones) {
            System.out.println("Leyendo valor de sensor en conexión: " + conexion);
            int valor = new Random().nextInt(1024); /
            System.out.println("Valor leído: " + valor);
        }
    }

    public void controlarSalidas() {
        System.out.println("Controlando salidas desde Arduino...");
    
        for (String conexion : conexiones) {
            System.out.println("Activando dispositivo conectado a: " + conexion);
          
        }
    }
}


class LDR {
    private int sensibilidad;
    private int valorLuz;

    public LDR(int sensibilidad) {
        this.sensibilidad = sensibilidad;
    }

    public void medirLuz() {
        System.out.println("Midiendo la luz con LDR...");
       
        this.valorLuz = new Random().nextInt(1024); 
        System.out.println("Valor de luz medido: " + valorLuz);
    }

    public boolean detectarCambios() {
        System.out.println("Detectando cambios en la luz...");
        
        int nuevoValorLuz = new Random().nextInt(1024); 
        int cambio = Math.abs(nuevoValorLuz - valorLuz);
        System.out.println("Cambio detectado: " + cambio);
        return cambio > sensibilidad;
    }
}

public class Main {
    public static void main(String[] args) {
    
        PanelSolarRotativo panel = new PanelSolarRotativo("Grande", "Silicio", true);
        panel.generarEnergia();
        panel.rotar();

        List<String> conexiones = List.of("Sensor1", "Sensor2", "Actuador1");
        Arduino arduino = new Arduino("Uno", conexiones);
        arduino.leerEntradas();
        arduino.controlarSalidas();

        LDR ldr = new LDR(50);
        ldr.medirLuz();
        boolean hayCambio = ldr.detectarCambios();
        System.out.println("¿Se detectó un cambio en la luz? " + hayCambio);
    }
}
