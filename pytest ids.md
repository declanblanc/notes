[Python](Python.md)

There's about a bajillion different ways to write Python tests but one I've been using quite a bit is ✨parametrized testing✨ which allows you to basically list all of tests you'd like to run before the testing function. 

So instead of doing:
```python
def test_add_1():
	assert add(2,3) == 5
def test_add_2():
	assert add(5,5) == 10

#...... etc.
```

Parametrized tests allow us to list each test like so:

```python
pytest.mark.parametrize(
	"var1,var2,answer",
	[
		(2,3,5),
		(5,5,10),
		(-5,8,3),
	]
)
def test_add(var1,var2,answer):
	assert add(var1,var2) == answer

```

ta-da!