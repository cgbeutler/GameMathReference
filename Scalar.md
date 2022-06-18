Scalars
=======

Don't be scared by the name. This page is just for single-number stuffs (as opposed to vectors that have several quantity components.)

## Sigmoid Functions

Sigmoid functions are surprisingly useful and I wish that I had discovered them sooner! They form an 's' shape between two horizontal asymptotes.
They are great for sliding between two different values (like 0 and 1.)

Unlike easing functions, however, they will _never_ reach either value and instead just get continually closer to them.

### Logistic Sigmoid Function

For values between 0 and 1. (Note: Uneven axis scales used in graph below)
![image](https://user-images.githubusercontent.com/9751923/174429161-948729c3-feab-4f67-97ab-7408f852c92e.png)

Written in C#. Altered to use a non-negative exponent calculation for a touch more speed:
```cs
public static double LogisticSigmoid( double x )
{
  var k = System.Math.Exp( x ); // Exp calculates Pow(e,x)
  return k / (1.0 + k);
}
```
Occasionally you may need to have a steeper or more gradual curve. For that, you can simply multiply x by a strength value before passing it to the equasion.
When the strenght is greater than one, the graph is horizontally squished and becomes steeper.
When the strength is a fraction, the graph is horizontall stretched and becomes more shallow.
A negative strength will horizontally flip the curve.

![logistic_sigmoid](https://user-images.githubusercontent.com/9751923/174429000-b827ae63-2a60-48b6-a639-12d227e2a156.gif)

(I use https://www.desmos.com/calculator any time I am working with functions. Even has an "animate" mode!)


### Hyperbolic Tangent Function

Basically the same function as above, just shifted to be between -1 and 1.
![image](https://user-images.githubusercontent.com/9751923/174429293-966f7011-e133-48d1-abfc-4dbb20252533.png)

Written in C#. Altered to use just one exponent call:
```cs
public static double HTanSigmoid( double x )
{
  var k = System.Math.Exp( 2 * x );
  return (-1+k)/(1+k);
}
```

Similarly, the x value can be pre-multiplied by a strength before being passed to the method in order to change the slope of the curve.
![hyperbolic_tan](https://user-images.githubusercontent.com/9751923/174429364-af0910df-1c67-46ff-b763-b26aae4eb713.gif)
