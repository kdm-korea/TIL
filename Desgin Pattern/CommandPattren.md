### Command Pattern

`command pattern` 

```C#
class Button
    {
        IOnClick onClick;

        public Button(IOnClick onClick) {
            this.onClick = onClick;
        }

        public void OnClick() {
            Console.WriteLine("Button Clicked");
            onClick.Execute();
        }

    }
```

```C#
interface IOnClick 
{
    void Execute();
}
```

```C#
class Lamp
    {
        private bool lampStatus = false;

        public bool LampStatus { get => lampStatus; set => lampStatus = value; }
    }
```

```C#
class LampEvent : IOnClick
    {
        private Lamp lamp;

        public LampEvent(Lamp lamp) {
            this.lamp = lamp;
        }

        public void Execute() {
            LampPower();
        }

        private void LampPower() {
            lamp.LampStatus = !lamp.LampStatus;

            if (lamp.LampStatus == true) {
                Console.WriteLine("LampPower On");
            }
            else {
                Console.WriteLine("LampPower Off");
            }
        }
    }
```

```C#
class Program
    {
        static void Main(string[] args) {
            Lamp lamp = new Lamp();
            IOnClick lampClick = new LampEvent(lamp);
            Button button = new Button(lampClick);

            button.OnClick();
        }
    }
```