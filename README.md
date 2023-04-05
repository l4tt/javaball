# javaball
Made a mockup of a ball going to left to right on someones screen
Can be compiled java 8+
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class BallBounce extends JPanel {

    private static final int BALL_SIZE = 50;
    private static final int DELAY = 10;
    private int x = 0;
    private int y = 0;
    private int xVelocity = 1;
    private int yVelocity = 1;

    public BallBounce() {
        setPreferredSize(new Dimension(600, 400));
        setBackground(Color.BLACK);
        Timer timer = new Timer(DELAY, new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                moveBall();
                repaint();
            }
        });
        timer.start();
    }

    private void moveBall() {
        x += xVelocity;
        y += yVelocity;
        if (x <= 0 || x >= getWidth() - BALL_SIZE) {
            xVelocity = -xVelocity;
        }
        if (y <= 0 || y >= getHeight() - BALL_SIZE) {
            yVelocity = -yVelocity;
        }
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.setColor(Color.RED);
        g.fillOval(x, y, BALL_SIZE, BALL_SIZE);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Ball Bounce");
        BallBounce ballBounce = new BallBounce();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.add(ballBounce);
        frame.pack();
        frame.setVisible(true);
    }
}
```
