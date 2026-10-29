# later task : create a chess game in java.


# Write a class chesspiece


### <<|CHESSPIECE|>> class
- Coordincate(x,y);
- Color color;
- Character name;
- move();

---
### whats the problem here in this class
- we are directly voilating the SRP 
- move() will be different for each piece 
- this class is having responsibility of each piece 
- there can be a function CanMove() 
- promotion logic will go to this class only and only pawn can promote so we have to handle that 


You have created a monster class 


---

### lets change the approach 

#### <<|CHESSPIECE|>> parent ABSTRACT class
- Coordincate(x,y);
- Color color;
- move(destincation x, destincation y);

#### <<|pawn|>> class
- override move()



#### <<|Rook|>>  class
- override move()


#### <<|Knight|>> class
- override move()

> is there any design flaw here 
> yessss

----

### approach 3

#### <<|CHESSPIECE|>> parent ABSTRACT class
- Coordincate(x,y);
- Color color;
- move(destincation x, destincation y);
- castle();

#### <<|pawn|>> class
- override move()
- castle();


#### <<|Rook|>>  class
- override move()
- castle();



#### <<|Knight|>> class
- override move()
- castle();


Not every one can castle only rook and king can castle ,
other pieces has noting to do with castling 

you will write a good method for chasle in king but for other pieces you will throw an exception

there is a problem with pawn class 
move()
if someone gave you the coordinate which is behind us, then its an illegal argument


The problem is the way we have designed the classes is forcing us to implement certain methods that we dont want to implement


---
# Liskov Substitution Principle

> Objects  of a child class should be AS-IS substitutable in the variable of a parent class


```java

Chesspiece K = new King();
Chesspiece k = new Knight();
Chesspiece p1 = new Pawn();


// 
p1.castle(); // will throw an exception
// but
K.castle(); 
// here we have to do so many custom handling 
```


#### problem that we observed 

- we can move the castle fn to only to king
- but
- think if we have a fn that is used by king and queen only or a fn used by knight, pawn and rook only so again and again we have to write the same implementation to all the classes again and again who want to implement the same methods 

---
---

may be in a Modified Chess :
    Rooks -> Rook + Knight
    Queen -> queen + Knight
    Knight -> bishop + king
    King -> Pawn + Queen + Bishop + Knight
    Some custom pieces or moves