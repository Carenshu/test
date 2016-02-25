import de.bezier.guido.*;

private Blob[][] blobs; 






void setup ()



{



  size(400, 400);



  // make the manager



  Interactive.make( this );

  blobs = new Blob[10][10];

  for (int r = 0; r < 10; r++)

    for (int c = 0; c < 10; c++)

      blobs[r][c] = new Blob(r, c);
}



void draw() {
}//empty






public class Blob



{



  private int r, c;



  private float x, y, width, height;

  private boolean marked;





  public Blob ( int rr, int cc )

  {



    width = 40;



    height = 40;



    r = rr;



    c = cc; 



    x = c*width;



    y = r*height;



    marked = Math.random() < .5;

    Interactive.add( this ); // register it with the manager
  }



  public boolean isMarked()

  {



    return marked;
  }



  public boolean isValid(int row, int col)

    //post condition: returns true if both row and col are valid, 
    //false otherwise



  {

    //your code here
   
      
if (r>9||c>9||r<0||c<0)

      return false;
  
  else
  
  return true;
  



  }


  public void mousePressed () 

  {



    if (marked == true)



    {


      marked = false;



      if (isValid(r, c-1) && blobs[r][c-1].isMarked())

        blobs[r][c-1].mousePressed();
        
       if (isValid(r,c+1)&& blobs[r][c+1].isMarked())
       blobs[r][c+1].mousePressed();
       
        if (isValid(r-1,c)&& blobs[r-1][c].isMarked())
      blobs[r-1][c].mousePressed();
      
       if (isValid(r+1,c)&& blobs[r+1][c].isMarked())
       blobs[r+1][c].mousePressed();
      //3 more recursive calls
    }
  }



  public void draw () 



  {    



    if (marked)



      fill(50);



    else 



    fill( 255 );






    rect(x, y, width, height);

    fill(0);
  }
}
