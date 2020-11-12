# OOP
- [ ] Section 6: Object Oriented Programming 00/19 | 1hr 48min
	- [ ] 091. Section Overview | 6min Resources
	- [ ] 092. OOP and FP | 4min
	- [ ] 093. OOP Introduction | 3min
	- [ ] 094. OOP1: Factory Functions | 8min Resources

  ## Questions
  - What did you find challenging?
  - What was new to you?
  - What do you feel confident on?
    - I have seen the idea of having a template function for creating objects.

  ```javascript
  // factory function make/create
  function createElf(name, weapon) {
    // we can also have closures here to hide properties from being changed.
    return {
      name: name,
      weapon: weapon,
      attack() {
        return 'attack with ' + weapon
      }
    }
  }

  const sam = createElf('Sam', 'bow');
  const peter = createElf('Peter', 'bow');

  sam.attack()
  ```

  - There's a need to share functionality of parts of the factory function
  
	- [ ] 095. OOP2: Object.create() | 8min Resources

  ## Questions
  - What did you find challenging?
  - What was new to you?
    - The creation of an "internal function" that accesses on outside function on the prototype chain, I don't remember seeing
    this implementation before.
  - What do you feel confident on?
    - I am confident that I can compose objects out of re-usable parts.

  ```javascript
  // Constructor Functions
  function Elf(name, weapon) {
    this.name = name;
    this.weapon = weapon;
  }

  Elf.prototype.attack = function() { 
    return 'attack with ' + this.weapon
  }
  const sam = new Elf('Sam', 'bow');
  const peter = new Elf('Peter', 'bow');
  sam.attack()
  ```

	- [ ] 096. OOP3: Constructor Functions | 13min Resources

  ## Questions
  - What did you find challenging?
  - What was new to you?
  - What do you feel confident on?
    - I've seen the use of constructor functions in previous lessons.

  ```javascript
  // Constructor Functions
  // Not returning anything here...
  // The "new" keyword
  function Elf(name, weapon) {
    this.name = name;
    this.weapon = weapon;
  }

  Elf.prototype.attack = function() { 
    return 'atack with ' + this.weapon
  }
  const sam = new Elf('Sam', 'bow');
  const peter = new Elf('Peter', 'bow');
  sam.attack()
  ```

  ```javascript
  class Elf {
    constructor(name, weapon) {
      this.name = name;
      this.weapon = weapon;
    }
    attack() {
      return 'atack with ' + this.weapon
    }
  }

  const fiona = new Elf('Fiona', 'ninja stars');
  console.log(fiona instanceof Elf) // 
  const ben = new Elf('Ben', 'bow');
  fiona.attack()
  ```

	- [ ] 099. OOP4: ES6 Classes | 9min Resources

  ## Questions
  - What did you find challenging?
  - What was new to you?
    - Subclassing, with the "extend" keyword
  - What do you feel confident on?
    - I'm confident working with JavaScript objects and prototypal inheritance.

    - The use of "prototype" syntax was unpopular.
    - The "class" keyword is syntactic sugar for the "new" keyword with the prototype.

    ```javascript
    class Character {
      constructor(name, weapon) {
        this.name = name;
        this.weapon = weapon;
      }
      attack() {
        return 'atack with ' + this.weapon
      }
    }

    class Elf extends Character { 
      constructor(name, weapon, type) {
        // console.log('what am i?', this); this gives an error
        super(name, weapon) 
        console.log('what am i?', this);
        this.type = type;
      }
    }

    class Ogre extends Character {
      constructor(name, weapon, color) {
        super(name, weapon);
        this.color = color;
      }
      makeFort() { // this is like extending our prototype.
        return 'strongest fort in the world made'
      }
    }

    const houseElf = new Elf('Dolby', 'cloth', 'house')
    // houseElf.makeFort() // error
    const shrek = new Ogre('Shrek', 'club', 'green')
    shrek.makeFort()
    ```
