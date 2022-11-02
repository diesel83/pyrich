## Setup

```bash
mkdir pyrich
cd pyrich
python3 -m venv venv
source venv/bin/activate
pip install rich
```

## Rich examples
Enter the REPL in the terminal by typing `python3`

### Simple print
```python
from rich import print
print("[blue]Astros[/blue] [red]SUCK[/red]!!! :poop: ")
print(locals())
```

### Pretty
```python
from rich import pretty
pretty.install()
locals()
```

### Inspect
```python
from rich import inspect
inspect("this is a string")
inspect("this is a string, methods=True")
```

### Console print
```python
from rich.console import Console
console = Console()
console.print("Astros suck", style="bold red")
console.log("Astros suck", style="bold red")
```

### Logging
```python
import logging
from rich.logging import RichHandler
FORMAT = "%(message)s"
logging.basicConfig(
    level="NOTSET", format=FORMAT, datefmt="[%X]", handlers=[RichHandler()]
)
log = logging.getLogger("rich")
log.info("Hello, World!")
```

### Tables

```python
from rich.console import Console
from rich.table import Table

table = Table(title="Star Wars Movies")

table.add_column("Released", justify="right", style="cyan", no_wrap=True)
table.add_column("Title", style="magenta")
table.add_column("Box Office", justify="right", style="green")

table.add_row("Dec 20, 2019", "Star Wars: The Rise of Skywalker", "$952,110,690")
table.add_row("May 25, 2018", "Solo: A Star Wars Story", "$393,151,347")
table.add_row("Dec 15, 2017", "Star Wars Ep. V111: The Last Jedi", "$1,332,539,889")
table.add_row("Dec 16, 2016", "Rogue One: A Star Wars Story", "$1,332,439,889")

console = Console()
console.print(table)
```

### Progress bar
```python
from time import sleep
from rich.progress import track

for step in track(range(10)):
    sleep(1)
    step
```
### Status
```python
from time import sleep
from rich.console import Console

console = Console()
tasks = [(f"task {n}" for n in range(1, 11))]

with console.status("[bold green]Working on tasks....") as status:
    while tasks:
        task = tasks.pop(0)
        sleep(1)
        console.log(f"{task} complete")
```

### Tracebacks
```python
from rich.traceback import install
install()
1 / 0
```
