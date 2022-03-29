# Exercise 5: NER

The goal of this exercise is to learn to use a Named entity recognition algorithm to detect entities. 

```
Apple Inc. is an American multinational technology company headquartered in Cupertino, California, that designs, develops, and sells consumer electronics, computer software, and online services. It is considered one of the Big Five companies in the U.S. information technology industry, along with Amazon, Google, Microsoft, and Facebook.
Apple was founded by Steve Jobs, Steve Wozniak, and Ronald Wayne in April 1976 to develop and sell Wozniak's Apple I personal computer, though Wayne sold his share back within 12 days. It was incorporated as Apple Computer, Inc., in January 1977, and sales of its computers, including the Apple I and Apple II, grew quickly.
 ```

1. Extract all named entities in the text as well as the label of the named entity.

2. The NER is also useful to remove ambigous entities. From a conceptual standpoint, disambiguation is the process of determining the most probable meaning of a specific phrase. For example in the sentence below, the word `apple` is present twice in the sentence. The first time to mention the fruit and the second to mention a company. Run the NER on this sentence and print the named entity, the `start_char`, the `end_char` and the label of the named entity. 

```
Paul eats an apple while watching a movie on his Apple device.
```
https://en.wikipedia.org/wiki/Named-entity_recognition