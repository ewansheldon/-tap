THE TAP METHOD
==============
A method that allows you to <i>tap into</i> an object to make changes, whilst making sure that what is returned is the object you're applying the method to.

A sad example:

<pre><code>2.3.0 :001 > zoo = ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"]

 => ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"] </code></pre>
 
You realise you don't need the last object in your array anymore:
 
<pre><code>2.3.0 :002 > zoo.pop

 => "harambe"</code></pre>
 
 Your popped item is returned and remembered fondly.
 
 However, to deflect attention from your poor popped item, you may want to use the #tap method:
 
 <pre><code>2.3.0 :001 > zoo = ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"]
 => ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"] 
2.3.0 :002 > zoo.tap {|zoo| zoo.pop}
=> ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse"]</pre></code>
 
 Tap allows you to return the array that you applied the method to, as well as saving the item that you fatefully popped:
 
 <pre><code>2.3.0 :001 > zoo = ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"]
=> ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"]
2.3.0 :002 > fallen_heroes = Array.new
=> [] 
2.3.0 :003 > zoo.tap {|zoo| fallen_heroes << zoo.pop}
=> ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse"]</pre></code>
