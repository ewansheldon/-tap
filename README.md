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

=> ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse"]</code></pre>
 
Tap allows you to return the array that you applied the method to, as well as saving the item that you fatefully popped:
 
<pre><code>2.3.0 :001 > zoo = ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"]

=> ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse", "harambe"]

2.3.0 :002 > fallen_heroes = Array.new

=> [] 

2.3.0 :003 > zoo.tap {|zoo| fallen_heroes << zoo.pop}

=> ["dog", "cat", "hamster", "guinea pig", "parrot", "seahorse"]

2.3.0 :004 > fallen_heroes

 => ["harambe"]</code></pre>


Similarly, if you want to create a new variable in a method without having that variable returned, you're not left with particularly clean code:

<pre><code>def create_registration_name(name)

    @registration_name = name.split.reverse.join(", ")

    name

end</code></pre>

The #tap method allows you to clean this up:

<pre><code>def create_registration_name(name)
   name.tap do |name|
   @registration_name = name.split.reverse.join(", ")
  end
end</code></pre>


With hashes, one possible use of #tap is to assign a new value to a key and return the full hash rather than the change you just made.

Rather than: 
<pre><code>2.3.0 :001 > pet_ages = {cat: 4, dog: 4, fish: 0, hamster: 1}

=> {:cat=>4, :dog=>4, :fish=>0, :hamster=>1}
 
2.3.0 :002 > pet_ages[:fish] = 1
 
=> 1 </code></pre>
 
You can tap into the hash:
 
<pre><code>2.3.0 :001 > pet_ages = {cat: 4, dog: 4, fish: 0, hamster: 1}
 
=> {:cat=>4, :dog=>4, :fish=>0, :hamster=>1} 
 
2.3.0 :002 > pet_ages.tap {|hash| hash[:fish] = 1}

=> {:cat=>4, :dog=>4, :fish=>1, :hamster=>1} </code></pre>
