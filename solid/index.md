# SOLID

- Single Responsibility Principle (SRP);
- Open Closed Principle (OCP);
- Liskov Substitution Principle;
- Interface Segregation Principle;
- Dependency Inversion Principle;

## Single-Responsibility Principle (SRP)

> "A class should have one, and only one reason to change."
> <footer>— Robert C Martin</footer>

## Open-Closed Principle (OCP)

> "Software entities should be open for extension but closed for modification"
> <footer>Bertrand Mayer, Object-Oriented Software Conclusion</footer>

## Liskov Substitution Principle (LSP)

> "If S is a subtype of T, then objects of type T may be replaced by objects of type S,
> without breaking the program"
> <footer>Barbara Liskov</footer>

```python
class Event:
    ...
    def meets_condition(self, event_data: dict) -> bool:
        return False

class LoginEvent(Event):
    def meets_condition(self, event_data: list) -> bool:
        # LSP violation: event_data is a list rather than dict
        return bool(event_data)

class LogoutEvent(Event):
    def meets_condition(self, event_data: dict, override: bool) -> bool:
        # LSP violation: the function signature has changed
        if override:
            return True
        ...
```

LSP violation detectable by static analysis (in most cases).

## Interface Segregation Principle (ISP)

> "Clients should not be forced to depend on methods they do not use."
> <footer>Robert C Martin</footer>

```python
from abc import ABCMeta, abstractmethod

class XMLEventParser(metaclass=ABCMeta):
    @abstractmethod
    def from_xml(xml_data: str):
        """Parse an event from a source in XML representation."""

class JSONEventParser(metaclass=ABCMeta):
    @abstractmethod
    def from_json(json_data: str):
        """Parse an event from a source in JSON format."""

class EventParser(XMLEventParser, JSONEventParser):
    """An event parser that can create an event from source data"""
    def from_xml(xml_data: str):
        pass

    def from_json(json_data: str):
        pass
```

## Dependency Inversion Principle (DIP)

> "High-level modules should not depend on low-level modules. Both should depend on
> abstractions. Abstractions should not depend on details. Details should depend on
> abstractions."
> <footer>Robert C. Martin</footer>
