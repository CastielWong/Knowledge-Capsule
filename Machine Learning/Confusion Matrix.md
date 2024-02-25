
- [Case](#case)
  - [Solution](#solution)
  - [Diagnostic](#diagnostic)
  - [Follow-up](#follow-up)


| Actual \ Predicted | 1 | 0 | |
| --- | --- | --- | --- |
| 1 | TP | FN | Actual Positive |
| 0 | FP | TN | Actual Negative |
| | Predicted Positive | Predicted Negative |  |

- Sensitivity = TP / (TP + FN)
- Specificity = TN / (TN + FP)


## Case
There are 0.1% people infected by a disease. There is a way to detect whether a person is infected or not, for whose sensitivity and specificity are both 99%.
Assuming John Doe is tested positive by this method, then what is the probability that John is truly infected?

### Solution
To find out the probability if one is actually infected when it's tested positive, what we need want to get is how many infected people tested positive among all infected people, which should be:
`TP / (TP + FP)`

Then the Confusion Matrix will look like:

|               | Positive          | Negative          |
| ---           | ---               | ---               |
| Infected      | 0.1% * 99% (TP)   | 0.1% * 1%   (FN)  |
| Uninfected    | 99.9% * 1% (FP)   | 99.9% * 99% (TN)  |

So the probability is:
`infected * Sensitivity / (infected * Sensitivity + (1 - infected) * (1 - Specificity)) `
= `0.1% * 99% / (0.1% * 99% + 99.9% * 1%)`
= 9.9 / (9.9 + 99.9)
= 9.02%

### Diagnostic
Assuming the population is 10,000. According to the infected rate, we would expect there are 10 people who are actually infected. Then the Confusion Matrix will be:

|               | Positive      | Negative      |
| ---           | ---           | ---           |
| Infected      | 10 * 99%      | 10 * 1%       |
| Uninfected    | 9,990 * 1%    | 9,990 * 99%   |

The probability will be derived by: 9.9 / (9.9 + 99.9) = 9.02%.

What makes this case counterintuitive is that there are only 10 people infected, but there could be 99.9 imaginary people infected as FP.

The gap is caused by the difference on Specificity, which is expected to be (10 - 9.9) people, but it was 99.9 due to the model's accuracy.
The infected rate is less than the Specificity.

### Follow-up
What is the probability if the same person is positive again for his second test?

This time, the infected rate needs to update from 0.1% to 9% because of his first test:

|               | Positive  | Negative  |
| ---           | ---       | ---       |
| Infected      | 9% * 99%  | 9% * 1%   |
| Uninfected    | 91% * 1%  | 91% * 99% |

So the probability will be:
`9% * 99% / (9% * 99% + 91% * 1%)`
= 891 / (891 + 91)
= 90.7%
