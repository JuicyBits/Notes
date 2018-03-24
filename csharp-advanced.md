## Generics
- Allows for code reusability without performance penalties brought on by casting object types
- Most likely, you will use existing generics, _not_ creating them

```
public class GenericList<T>
{
  public void Add(T value)
  {

  }

  public T this[int index]
  {
    get { ... }
  }
}
```

### Constraints
```
 public int Max(int a, int b)
{
    return a > b ? a : b;
}

// OR

public T Max<T>(T a, T b) where T : IComparable
{
    return a.CompareTo(b) > 0 ? a : b;
}
```
- Can be applied to class or method:
  - `where T : IComparable`
  - `where T : Product`
  - `where T : struct`
  - `where T : class`
  - `where T : new()`

## Dictionaries
- Use a hash table to store and retrieve objects (great performance advantages)
- Key / value pairs

## Delegates
- An object that knows how to call a method (_or group of methods_)
- A reference to a function

### Why use delegates?
- For designing extensible and flexible applications (e.g. frameworks)

- `public delegate void PhotoFilterHandler(Photo photo);`
  - This delegate can handle methods with a `void` signature that take `Photo` as a parameter

### Existing Delegates
- `System.Action<>`
- `System.Func<>`

### Interfaces or Delegates?
- Use a delegate when:
  - An eventing design pattern is used
  - The caller doesn't need to access the other properties or methods on the object implementing the method

## Lambda Expression
- An anonymous method
- No access modifier
- No name
- No return statement
- Similar to `arrow functions` in JS
- Has access to all arguments passed, as well as all properties within class expression is called in

### Why?
- Convenience

- `[args] => [expression]`
- `x => ...`
- `() => ...`
- `(x, y, z) => ...`

```
func<int, int> square = number => number*number;
square(5; // 25
```

## Events and Delegates
### Events
- A mechanism for communicating between objects
- Used in building _Loosely Coupled Applications_
- Helps extend applications
- Allows for publishers of event to alert subscribers of event when necessary

### Delegates
- Agreement / Contract between **Publisher** and **Subscriber**
- Determines the signature of the event handler method in **Subscriber**

1. Define a delegate
2. Define an event based on that delegate
3. Raise the event

```
class Program
{
  static void Main(string[] args)
  {
    var video = new Video() { Title = "Video 1"}
    var videoEncoder = new VideoEncoder(); // Publisher
    var mailService = new MailService(); // Subscriber

    videoEncoder.VideoEncoded += mailService.OnVideoEncoded;

    videoEncoder.Encode(video);
  }
}
```

```
public class VideoEncoder
{
  public delegate void VideoEncodedEventHandler(object source, EventArgs args);

  public event VideoEncodedEventHandler VideoEncoded;

  public void Encode(Video video)
  {
    Console.WriteLine("Encoding Video...")
    Thread.Sleep(3000); // Simulates encoding implementation...

    OnVideoEncoded();
  }

  protected virtual void OnVideoEncoded()
  {
    if (VideoEncoded != null)
      VideoEncoded(this, EventArgs.Empty);
  }
}
```
- Can use `public event EventHandler VideoEncoded` without needing `public delegate void VideoEncodedEventHandler(object source, EventArgs args);`
- `OnVideoEncoded()`
  - Fires `VideoEncoded` event handler
```
public class MailService
{
  public void OnVideoEncoded(object source, EventArgs e)
  {
    Console.WriteLine("MailService: Sending an email..."); // Simulates MailService...
  }
}
```
