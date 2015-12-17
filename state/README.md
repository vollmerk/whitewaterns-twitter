# Twitter tweet state

Files in this directory hold the last tweet state in a [item].json
where ITEM is it's unique name in the source.json file in the root

Entry format:
```
{
	"Unique Resource Name": {
		"state" : "up" / "down",
		"date": "RFC date",
		"lastTweet": "RFC date",
	}
}
```
