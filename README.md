# ojs(o$) - Simple Oject Oriented JS Library



Browser Support

    IE 6+, FF, Chrome, Safari, Opera, Konqueror, Android(4.0+), iOS, ...



Keywords(internal names)

    Class       - Class type
    Private     - access modifier
    Protected   - access modifier
    Public      - access modifier
    Inherited   - ancestor method call
    Create      - constructor function



code exemaple 1

    Pet = Class({
        Private:{
            name: "Pet",
            nick: "pet",
            getNick: function() {return(this.nick);}
        },
        Protected:{
            getName: function() {return(this.name);}
        },
        Public:{
            showName: function() {log(this.getName());},
            showNick: function() {log(this.getNick());},
            Create: function(n) {if(n) this.name = n;}
        }
    })
    
    Dog = Pet({
    })
    
    Cat = Pet({
        Public:{
            dog: new Dog("mewoo"),
            showName: function() {this.Inherited();},
            showNick: function() {this.Inherited();}
        }
    })
    
    var memory = new Dog("dog");
    var leak = new Cat();

    log("Class.ClassName(): " + Class.ClassName());
    log("Pet.ClassName(): " + Pet.ClassName());
    log("Cat.ClassName(): " + Cat.ClassName());
    log("Dog.ClassName(): " + Dog.ClassName());
    log("Cat.Ancestor.ClassName(): " + Cat.Ancestor.ClassName());
    log("Cat.Ancestor.Ancestor.ClassName(): " + Cat.Ancestor.Ancestor.ClassName());
    log("leak.Type == Cat: " + (leak.Type == Cat));
    log("leak.Type.ClassName(): " + leak.Type.ClassName());
    log("typeof(leak): " + typeof(leak));
    log("leak instanceof Class: " + (leak instanceof Class));
    log("leak instanceof Pet: " + (leak instanceof Pet));
    log("leak instanceof Cat: " + (leak instanceof Cat));
    log("leak instanceof Dog: " + (leak instanceof Dog));
    log("")
    memory.showNick();
    memory.showName();
    leak.showNick();
    leak.showName();
    leak.t.showName();
    
exemple output 1

    Class.ClassName(): Class
    Pet.ClassName(): Pet
    Cat.ClassName(): Cat
    Dog.ClassName(): Dog
    Cat.Ancestor.ClassName(): Pet
    Cat.Ancestor.Ancestor.ClassName(): Class
    leak.Type == Cat: true
    leak.Type.ClassName(): Cat
    typeof(leak): object
    leak instanceof Class: true
    leak instanceof Pet: true
    leak instanceof Cat: true
    leak instanceof Dog: false
    pet
    dog
    pet
    Pet
    mewoo



