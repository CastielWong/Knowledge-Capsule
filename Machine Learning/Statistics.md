
- [Simpson's Paradox](#simpsons-paradox)
  - [Quintessence](#quintessence)
- [Reference](#reference)

## Simpson's Paradox

|        | Solution A       | Solution B       |
|--------|------------------|------------------|
| Case A | 90% = 90 / 100   | 80% = 640 / 800  |
| Case B | 30% = 300 / 900  | 25% = 50 / 200   |
| Total  | 39% = 390 / 1000 | 69% = 690 / 1000 |

Though solution A outperform solution B in both cases, the accuracy of solution A underperforms when combining both cases number.

The reason why this paradox occurs is because:
- The amount of both cases are not equally distributed
- The final accuracy is inclined to the case which gets more amount
- The final accuracy weights more on the predominant case

### Quintessence
The drug effect on different genders experiment:
|            | Male            | Female        | Weighted Average | Arithmetic Mean           |
|------------|-----------------|---------------|------------------|---------------------------|
| Experiment | 40.0% =  8 / 20 | 7.5% = 3 / 40 | 18.3% = 11 / 60  | 23.75% = (40.0 + 7.5) / 2 |
| Control    | 30.0% = 12 / 40 | 5.0% = 1 / 20 | 21.7% = 13 / 60  | 17.50% = (30.0 + 5.0) / 2 |
| Ensemble   | 33.3% = 20 / 60 | 6.7% = 4 / 60 | 20.0% = 24 / 120 | 20.00% = (33.3 + 6.7) / 2 |

We could tell the drug is taking effects from __Weighted Average__ as the morbidity decreased to 18.3% from 21.7.

However, when we let the gender group consistently equal and check __Arithmetic Mean__, the morbidity was actually increased, from 17.50% to 23.75%.

The paradox here happens at the gender difference, for which such drug has different effects between genders. It harms male more than female. In that case, so long as there is more male than female in control group, it's likely the __Weighted Average__ would look better.


## Reference
- 有哪些违背直觉的数学问题: https://www.zhihu.com/question/41408857/answer/107650697
- What is a Point Estimate in Statistics: https://www.statology.org/point-estimate/
