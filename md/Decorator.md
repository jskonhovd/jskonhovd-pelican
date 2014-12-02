HFDP - Decorator pattern
########################
:date: 2012-12-02 18:30
:category: Programming
:tags: Java
:author: Jeffrey Skonhovd
:excerpt: HFDP


Today, I read a little bit of Head First Design Patterns, while nervously reloading the 49ers game on NFL.com. I really wish there was a place I could watch the game and still study. I would feel a little weird showing up at bar with laptop and a textbook. The lost today was disappointing, but I am still confident that Kaepernick is the correct choice going forward at quarterback.

So, The decorator pattern is a design pattern that attaches additional responsibilities to an object dynamically. The decorator has practical applications in the Java.IO package. The following is "Whip" class that was an exercise in the book.

.. code-block:: java

    package starBuzz_HFDP;

    public class Whip extends CondimentDecorator {
        Beverage beverage;
    
        public Whip(Beverage beverage){
        
            this.beverage = beverage;
        }
        @Override
        public String getDescription() {
        // TODO Auto-generated method stub
        return beverage.getDescription() + ", Whip";
    }

        @Override
    public double cost() {
        // TODO Auto-generated method stub
        return .56 + beverage.cost();
    }

    }

The next block of code is the very similar "Soy" class, which is also an exercise. These code samples are pretty straight forward from the book.

.. code-block:: java

    package StarBuzz_HFDP;

    public class Soy extends CondimentDecorator {
        Beverage beverage;
    
    
        public Soy(Beverage beverage) {
            this.beverage = beverage;
        }
    
        public String getDescription() {
            // TODO Auto-generated method stub
            return beverage.getDescription() + ", Soy!!!";
        }

        @Override
        public double cost() {
            // TODO Auto-generated method stub
            return 0.20 + beverage.cost();
        }

    }

Finally, I will end with my version of StarBuzz class, which is just a main method.

.. code-block:: java

    package StarBuzz_HFDP;

    public class StarBuzzCoffee {

    
    // * @param args
    
        public static void main(String[] args) {
        // TODO Auto-generated method stub
        Beverage beverage = new Espresso();
        System.out.println(beverage.getDescription()
                + " $" + beverage.cost());
        
        Beverage beverage2 = new HouseBlend();
        beverage2 = new Mocha(beverage2);
        beverage2 = new Soy(beverage2);
        beverage2 = new Whip(beverage2);
        System.out.println(beverage2.getDescription()
                + " $" + beverage2.cost());
                
    }

    }


