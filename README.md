# Gumbo
New programming language completely comprised of Streams and Sinks.    WIP !!!

Example

-------------------------------------------------------------------------------------------

    // Define Streaming function to add a number.
    def add(x){
       // Every Function has an implicit argument 'it' that represents the 
       //  stream value.
       it + x
    }

    // Define Streaming function to determine if number is odd.
    def isOdd(){
       (it % 2) == 0
    }
    
    
    [] -> x                        // stream empty array into new Variable x.

    x -> add(2) -> z               // stream x into function call add(2)  .. 'implicitly calls add(Xi,2) for each i in stream x'
                                   //   and stream function result to new var z.
    
    z -> {                         // stream z into a Block with conditional logic
      case isOdd {                 // stream 'it' into isOdd and branch by return value      
         True : it -> add(1)       // stream  it to add(1)
         otherwise : it            // stream  it
      }
    } -> y                         // stream result into new variable y

    y |> print                     // Sink all events in y and print to screen.
    
    
    
    // Now stream values into x and it starts the show
    
    [1,2,3,4] -> x
 ------------------------------------------------------------------------------------


