---
id: exam_2025_B_A_Open_q3
title: Smart Home Design Patterns
year: 2025
semester: B
moed: A
type: Open
language: Hebrew
topics:
- Design patterns - General
- WMS - Observer
- Design patterns - Command
skills:
- System Design
- Design Patterns Application
- UML
- Programming
---

## Question
הנך נדרש לעצב מערכת תוכנה לניהול בית חכם אשר שולטת במכשירים שונים (למשל נורות, מזגנים ודוד). במערכת צריכות להיות המחלקות הבאות : • `Door, AirConditioner, Boiler, Lights`: מחלקות עבור מכשירים חשמליים • `Security, ControlApp, HistoryFile`: מחלקות עבור קבלת עדכונים מהמכשירים להלן קוד (חלקי) של מחלקת `AirConditioner` ```java public class AirConditioner{ private void int temperature; public void turnOn(){...} public void turnoff(){ ... } public void setTemperature(int temp){ temperature = temp} } ``` המערכת נדרשת לעמוד בדרישות הבאות: 1. המשתמש יכול להגדיר פעולת מאקרו שמבצעת רצף פעולות על מספר מכשירים (למשל פעולת מאקרו "לילה טוב" תבצע כיבוי נורות, הדלקת מזגן, סגירת תריסים). המערכת צריכה לספק דרך אחידה לשליטה במכשירים. 2. המערכת צריכה לאפשר מעקב אחרי מצב המכשירים (למשל האם מנורה דלוקה/כבויה) ולשלוח עדכון בכל פעם שמתרחש שינוי במצב. להלן העיצוב המתוכנן למעקב אחרי המכשירים (נרצה לאפשר עדכון של העיצוב בעתיד, תוך שמירה על OCP) • המופע של `ControlApp` יקבל עדכונים מהמזגן ומהדוד • המופע של `HistoryFile` יקבל עדכונים מהדלת ומהדוד • המופע של `Security` יקבל עדכונים מהדלת סעיף א (10 נקודות) השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. אין צורך לכתוב את הקוד של `Lights, Boiler, Security, ControlApp`. כאן יש לענות רק על שאלה 3א (אם כתבת בטעות את פתרון שאלה 3א במקום אחר, ציין זאת כאן במפורש) סעיף ב (10 נקודות) כתוב את הקוד לאתחול המערכת עם הדרישות הבאות : `Door, AirConditioner, Boiler` אתחול מופעים של המכשירים החשמליים אתחול מופעי המחלקות שמקבלות מהם עדכונים (בכל עדכון, המופע ידפיס הודעה מתאימה, יש לתכנן את המערכת כך שתתמוך בפעולות מגוונות) : במידת הצורך עדכן את הקוד של המחלקות שכתבת בסעיף א. אתחול פעולת מאקרו שכוללת את הפעולות הבאות : • הדלקת המזגן • קביעת הטמפרטורה ל-25 מעלות • כיבוי דוד • כיבוי נורות כאן יש לענות רק על שאלה 3ב (אם כתבת בטעות את פתרון שאלה 3ב במקום אחר, ציין זאת כאן במפורש)

## Answer
**סעיף א: תבניות עיצוב וקוד**

**תבניות עיצוב בשימוש:**
1.  **Command Pattern (פקודה):** עבור דרישה 1 (פעולות מאקרו ושליטה אחידה במכשירים).
2.  **Observer Pattern (צופה):** עבור דרישה 2 (מעקב אחרי מצב המכשירים וקבלת עדכונים).

**תרשים מחלקות (תיאור מילולי):**
*   **Command Pattern:**
    *   `Command` (Interface): עם מתודה `execute()`. (ממשק הפקודה)
    *   `DeviceCommand` (Abstract Class): מחלקה אב מופשטת לפקודות מכשירים, מקבלת `Device` בבנאי.
    *   `TurnOnCommand`, `TurnOffCommand`, `SetTemperatureCommand` (Concrete Commands): מחלקות קונקרטיות המממשות את `Command` ומבצעות פעולות ספציפיות על מכשירים (לדוגמה, `TurnOnCommand` מקבלת `Device` בבנאי וקוראת ל-`device.turnOn()`).
    *   `MacroCommand` (Composite Command): מחלקה המממשת את `Command` ומכילה רשימה של אובייקטי `Command`. מתודת `execute()` שלה עוברת על כל הפקודות ברשימה ומפעילה אותן. (מאפשרת הרכבת פקודות).
*   **Observer Pattern:**
    *   `Subject` (Interface): עם מתודות `registerObserver(Observer o)`, `removeObserver(Observer o)`, `notifyObservers()`. (ממשק הנושא)
    *   `Observer` (Interface): עם מתודה `update(String deviceId, String state)`. (ממשק הצופה)
    *   `SmartDevice` (Abstract Class): מחלקה אב מופשטת למכשירים חכמים, מממשת את `Subject`. מכילה רשימה של `Observer`ים. כאשר מצב המכשיר משתנה, היא קוראת ל-`notifyObservers()`.
    *   `AirConditioner`, `Door`, `Boiler`, `Lights` (Concrete Subjects/Devices): יורשות מ-`SmartDevice` (או מממשות `Subject` ישירות). כאשר מצבן משתנה (לדוגמה, `turnOn()`, `setTemperature()`), הן קוראות ל-`notifyObservers()`.
    *   `ControlApp`, `HistoryFile`, `Security` (Concrete Observers): מממשות את `Observer` ומטפלות בעדכונים שהן מקבלות (לדוגמה, מדפיסות הודעה).

**קוד עבור המחלקות שצוירו (חלקי):**

```java
// Command Pattern
interface Command {
    void execute();
}

// Base Device interface for commands (optional, but good for abstraction)
interface Device {
    String getId();
    void turnOn();
    void turnOff();
    void setTemperature(int temp);
    // ... other device specific methods
}

class TurnOnCommand implements Command {
    private Device device;

    public TurnOnCommand(Device device) {
        this.device = device;
    }

    @Override
    public void execute() {
        device.turnOn();
    }
}

class SetTemperatureCommand implements Command {
    private AirConditioner ac;
    private int temperature;

    public SetTemperatureCommand(AirConditioner ac, int temperature) {
        this.ac = ac;
        this.temperature = temperature;
    }

    @Override
    public void execute() {
        ac.setTemperature(temperature);
    }
}

class MacroCommand implements Command {
    private List<Command> commands = new ArrayList<>();

    public void addCommand(Command command) {
        commands.add(command);
    }

    @Override
    public void execute() {
        for (Command command : commands) {
            command.execute();
        }
    }
}

// Observer Pattern
interface Observer {
    void update(String deviceId, String state);
}

interface Subject {
    void registerObserver(Observer o);
    void removeObserver(Observer o);
    void notifyObservers();
}

abstract class SmartDevice implements Subject, Device {
    private List<Observer> observers = new ArrayList<>();
    protected String id;
    protected String state;

    public SmartDevice(String id) {
        this.id = id;
        this.state = "Off"; // Default state
    }

    @Override
    public String getId() {
        return id;
    }

    @Override
    public void registerObserver(Observer o) {
        observers.add(o);
    }

    @Override
    public void removeObserver(Observer o) {
        observers.remove(o);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(id, state);
        }
    }

    // Common device methods, will notify observers on state change
    @Override
    public void turnOn() {
        System.out.println(id + " is turning ON.");
        this.state = "On";
        notifyObservers();
    }

    @Override
    public void turnOff() {
        System.out.println(id + " is turning OFF.");
        this.state = "Off";
        notifyObservers();
    }

    @Override
    public void setTemperature(int temp) {
        // Specific to AirConditioner, but included here for simplicity in SmartDevice
        // In a real system, this would be in AirConditioner and cast might be needed
        System.out.println(id + " temperature set to " + temp + ".");
        this.state = "Temperature: " + temp;
        notifyObservers();
    }
}

class AirConditioner extends SmartDevice {
    private int temperature;

    public AirConditioner(String id) {
        super(id);
        this.temperature = 20;
    }

    @Override
    public void setTemperature(int temp) {
        this.temperature = temp;
        super.setTemperature(temp); // Call super to notify observers
    }

    public int getTemperature() {
        return temperature;
    }
}

class Door extends SmartDevice {
    public Door(String id) {
        super(id);
        this.state = "Closed";
    }

    public void open() {
        System.out.println(id + " is opening.");
        this.state = "Open";
        notifyObservers();
    }

    public void close() {
        System.out.println(id + " is closing.");
        this.state = "Closed";
        notifyObservers();
    }

    @Override
    public void turnOn() { /* Not applicable */ }
    @Override
    public void turnOff() { /* Not applicable */ }
    @Override
    public void setTemperature(int temp) { /* Not applicable */ }
}

class Boiler extends SmartDevice {
    public Boiler(String id) {
        super(id);
        this.state = "Off";
    }
}

class Light extends SmartDevice {
    public Light(String id) {
        super(id);
        this.state = "Off";
    }
}

// Concrete Observers (simplified for example)
class ControlApp implements Observer {
    @Override
    public void update(String deviceId, String state) {
        System.out.println("ControlApp received update: " + deviceId + " is " + state);
    }
}

class HistoryFile implements Observer {
    @Override
    public void update(String deviceId, String state) {
        System.out.println("HistoryFile logging: " + deviceId + " changed to " + state);
    }
}

class Security implements Observer {
    @Override
    public void update(String deviceId, String state) {
        System.out.println("Security system alert: " + deviceId + " is " + state);
    }
}
```

**סעיף ב: קוד אתחול המערכת**

```java
import java.util.ArrayList;
import java.util.List;

public class SmartHomeSystem {
    public static void main(String[] args) {
        // 1. אתחול מופעים של המכשירים החשמליים
        AirConditioner ac = new AirConditioner("LivingRoom AC");
        Door frontDoor = new Door("Front Door");
        Boiler waterHeater = new Boiler("Water Heater");
        Light livingRoomLight = new Light("LivingRoom Light");

        // 2. אתחול מופעי המחלקות שמקבלות מהם עדכונים (Observers)
        ControlApp controlApp = new ControlApp();
        HistoryFile historyFile = new HistoryFile();
        Security security = new Security();

        // רישום צופים למכשירים הרלוונטיים
        // ControlApp מקבל עדכונים מהמזגן והדוד
        ac.registerObserver(controlApp);
        waterHeater.registerObserver(controlApp);

        // HistoryFile מקבל עדכונים מהדלת והדוד
        frontDoor.registerObserver(historyFile);
        waterHeater.registerObserver(historyFile);

        // Security מקבל עדכונים מהדלת
        frontDoor.registerObserver(security);

        System.out.println("--- Initializing Devices and Observers ---");
        ac.turnOff(); // Initial state
        frontDoor.close();
        waterHeater.turnOff();
        livingRoomLight.turnOff();
        System.out.println("----------------------------------------\n");

        // 3. אתחול פעולת מאקרו "לילה טוב"
        MacroCommand goodNightMacro = new MacroCommand();

        // הדלקת המזגן (לצורך הדגמה, נניח שזה חלק מהמאקרו)
        goodNightMacro.addCommand(new TurnOnCommand(ac));
        // קביעת הטמפרטורה ל-25 מעלות
        goodNightMacro.addCommand(new SetTemperatureCommand(ac, 25));
        // כיבוי דוד
        goodNightMacro.addCommand(new TurnOffCommand(waterHeater));
        // כיבוי נורות
        goodNightMacro.addCommand(new TurnOffCommand(livingRoomLight));
        // סגירת דלת (אם פתוחה)
        goodNightMacro.addCommand(new Command() {
            @Override
            public void execute() {
                if (frontDoor.state.equals("Open")) {
                    frontDoor.close();
                }
            }
        });

        System.out.println("--- Executing 'Good Night' Macro ---");
        goodNightMacro.execute();
        System.out.println("------------------------------------\n");

        // דוגמה לפעולה נוספת
        System.out.println("--- Manual Operation: Turn on AC ---");
        ac.turnOn();
        System.out.println("------------------------------------\n");
    }
}
```
