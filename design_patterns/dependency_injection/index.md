# Dependency injection

Dependencies are objects the specific class are depends on.

An example: a computer needs a processor, RAM, a hard drive and a graphics card. These
single components are computer's dependencies.

Without dependency injection we create components in the computer class:

```python
class Computer:
    def __init__(self):
        self.processor = Processor("Intel i7")
        self.ram = RAM(32)
        self.hard_drive = HardDrive(1024)
        self.graphics_card = GraphicsCard("NVIDIA GeForce")


computer1 = Computer()
computer2 = Computer()
```

Without dependency injection every computer that we create has the same specs and if we
change the parameters of some dependency, it will change for all computers.

Dependency injection help to solve this problem.

## Constructor injection

```python
class Computer:
    def __init__(
        self,
        processor: Processor,
        ram: RAM,
        hard_drive: HardDrive,
        graphics_card: GraphicsCard,
    ):
        self.processor = processor,
        self.ram = ram,
        self.hard_drive = hard_drive,
        self.graphics_card = graphics_card


computer1 = Computer(
    processor=Processor("Intel i7"),
    ram=RAM(32),
    hard_drive=HardDrive(1024),
    graphics_card=GraphicsCard("NVIDIA GeForce"),
)

computer2 = Computer(
    processor=Processor("AMD Ryzen"),
    ram=RAM(16),
    hard_drive=HardDrive(2048),
    graphics_card=GrahpicsCard("AMD"),
)
```


