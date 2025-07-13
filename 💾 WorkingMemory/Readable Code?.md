If I were to take the checks that I do in `main.py` for running the dispatch function or the creator command, and pull comparison operators of the if statements out into functions, it may feel more readable. 
```python title=before
if (
	message_content is not None
	and message_subtype is None
	and re.search(byte_pattern, message_content)
):
	# blah blah
```

This block of code, rewritten in English, says:

If the message is not empty, and is a normal message (not a reply, bot message, etc), and it contains the matching command prefix

So then what if I did something like this:
```python title=after
def is_valid_message(message):
	if ( 
		message.get['text'] is not None
		and message.get['subtype'] is none
		and re.search(byte_pattern, message_content)
	):
		return True
	return False


if (is_valid_byte_message(message)):
	# blah blah
```
The if statement by itself of course is now much easier to read and understand at a glance. But if you were trying to read and follow the logic of my code, is it now just more of a pain to have to store in your mind exactly what that function does? 