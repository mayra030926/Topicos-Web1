# Topicos-Web1
Sitio Web para la creación de programas en la clase de Topicos
-----------------------------

package tarea4;
import java.awt.Color;
import java.awt.Graphics;

public class MiLinea {

    private int x1; // coordenada x del primer punto final
    private int y1; // coordenada y del primer punto final
    private int x2; // coordenada x del segundo punto final
    private int y2; // coordenada y del segundo punto final
    private Color miColor; // el color de esta figura

// constructor con valores de entrada
    public MiLinea(int x1, int y1, int x2, int y2, Color color) {
        this.x1 = x1; // establece la coordenada x del primer punto final
        this.y1 = y1; // establece la coordenada y del primer punto final
        this.x2 = x2; // establece la coordenada x del segundo punto final
        this.y2 = y2; // establece la coordenada y del segundo punto final
        miColor = color; // establece el color
    } // fin del constructor de MiLinea

// Dibuja la línea en el color específico
    public void dibujar(Graphics g) {
        g.setColor(miColor);
        g.drawLine(x1, y1, x2, y2);
    } // fin del método dibujar
} // fin de la clase MiLinea
-------------------------------------------
package tarea4;
import java.awt.Color;
import java.awt.Graphics;

public class MiOval  {
private int x; // coordenada x del primer punto final
private int y; // coordenada y del primer punto final
private int w; // coordenada x del segundo punto final
private int h;// coordenada y del segundo punto final
private Color miColor; // el color de esta figura

// constructor con valores de entrada
public MiOval( int x, int y, int w, int h, Color color ){
this.x = x; // establece la coordenada x del primer punto final
this.y = y; // establece la coordenada y del primer punto final
this.w = w; // establece la coordenada x del segundo punto final
this.h = h; // establece la coordenada y del segundo punto final

miColor = color; // establece el color
} // fin del constructor de MiLinea

// Dibuja la línea en el color específico
public void dibujar( Graphics g )
{



g.setColor( miColor );
g.drawOval ( x,  y,  w, h);
g.fillOval ( x,  y,  w,  h  );
} // fin del método paintComponent
} // fin de la clase LineasRectsOvalosJPane


-------------------------------
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package tarea4;

import java.awt.Color;
import java.awt.Graphics;

public class MiRectangulo {

    private int x; 
    private int y; 
    private int w; 
    private int h;
    private Color miColor; 
    
    public MiRectangulo(int x, int y, int w, int h, Color color) {
        this.x = x; 
        this.y = y; 
        this.w = w; 
        this.h = h;

        miColor = color; 
    } 


    public void dibujar(Graphics g) {

        g.setColor(miColor);
        g.drawRect(x, y, w, h);
        g.fillRect(x, y, w, h);
    } 
} 

------------------
package tarea4;

import javax.swing.JFrame;

public class PruebaDibujo {

    public static void main(String args[]) {
        PanelDibujo panel = new PanelDibujo();
        JFrame aplicacion = new JFrame();
        

        aplicacion.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        aplicacion.add(panel);
        aplicacion.setSize(300, 300);
        aplicacion.setVisible(true);
    } // fin de main
} // fin de la clase PruebaDibujo
--------------------
package tarea4;

import java.awt.Color;
import java.awt.Graphics;
import java.util.Random;
import javax.swing.JPanel;


public class PanelDibujo extends JPanel {

    private Random numerosAleatorios = new Random();
    private MiLinea[] linea; // arreglo de lineas
    private MiOval oval[];
    private MiRectangulo rect[]; 
 // constructor, crea un panel con figuras al azar

    public PanelDibujo() {
        setBackground(Color.WHITE);
        oval = new MiOval[1 + numerosAleatorios.nextInt(1)];
        rect = new MiRectangulo[1 + numerosAleatorios.nextInt(1)];
        linea = new MiLinea[1 + numerosAleatorios.nextInt(1)];
// _______________________ RECTANGULO _____________________________
        for (int cuenta = 0; cuenta < rect.length; cuenta++) {

            int x1 = numerosAleatorios.nextInt(200);
            int y1 = numerosAleatorios.nextInt(200);
            int x2 = numerosAleatorios.nextInt(200);
            int y2 = numerosAleatorios.nextInt(300);

            Color color = new Color(numerosAleatorios.nextInt(250),
                    numerosAleatorios.nextInt(250), numerosAleatorios.nextInt(250));

            rect[cuenta] = new MiRectangulo(x1, y1, x2, y2, color);
        } // fin de for

// ______________________ LINEAS __________________________________________
// crea lineas
        for (int cuenta = 0; cuenta < linea.length; cuenta++) {

            int x1 = numerosAleatorios.nextInt(300);
            int y1 = numerosAleatorios.nextInt(300);
            int x2 = numerosAleatorios.nextInt(300);
            int y2 = numerosAleatorios.nextInt(450);

// genera un color aleatorio
            Color color = new Color(numerosAleatorios.nextInt(250),
                    numerosAleatorios.nextInt(250), numerosAleatorios.nextInt(250));

            linea[cuenta] = new MiLinea(x1, y1, x2, y2, color);
        } // fin de for
//_______________________ OVALO _________________________
        for (int cuenta = 0; cuenta < oval.length; cuenta++) {
            int x = numerosAleatorios.nextInt(400);
            int y = numerosAleatorios.nextInt(350);
            int w = numerosAleatorios.nextInt(400);
            int h = numerosAleatorios.nextInt(500);
            
            

// genera un color aleatorio
            Color color = new Color(numerosAleatorios.nextInt(250),
                    numerosAleatorios.nextInt(250), numerosAleatorios.nextInt(250));

// agrega la línea a la lista de líneas a mostrar en pantalla
            oval[cuenta] = new MiOval(x, y, w, h, color);
        }
    } // fin del constructor de PanelDibujo

// para cada arreglo de figuras, dibuja las figuras individuales
    public void paintComponent(Graphics g) {
        super.paintComponent(g);

// dibuja las líneas
        for (MiLinea linea : linea) {
            linea.dibujar(g);
        }
// dibuja las ovalos
        for (MiOval ovalos : oval) {
            ovalos.dibujar(g);
        }
// dibuja las rectangulos
        for (MiRectangulo rectangulos : rect) {
            rectangulos.dibujar(g);
        }
    }

// fin del método paintComponent
}
