# Vector 3D

## Length

```csharp
public float Length( Vector3 v )
  => Math.Sqrt( v.x*v.x + v.y*v.y + v.z*v.z );
```

The sqrt operation is a lot to compute, so sometimes a `LengthSquared` is better:

```csharp
public float LengthSquared( Vector3 v )
  => v.x*v.x + v.y*v.y + v.z*v.z;
```


## Dot Product

The dot product is commutative, meaning order does not matter.

The common, simplified explanation of what the dot product does is that it "projects" one vector onto another:

![](./img/dot_product.png)

This projection does not have to hit the other vector, it just project onto that vector as an infinite line.

The dot product will return a negative value if projected onto the other side of the origin like so:

![](./img/dot_product2.png)

### Dot product function
```csharp
public float Dot( this Vector3 a, Vector3 b )
  => a.x*b.x + a.y*b.y + a.z*b.z;
```


## Projection

The dot product returns a number (aka a scalar value,) _not_ a vector.
To perform a projection and get back a vector, you can do so _using_ the dot product and the normal of the target vector. This operation is not commutative.

### Project function
```csharp
public Vector3 Project( Vector3 a, Vector3 b )
  => a.Dot( b ) * b.Normalized();
```
