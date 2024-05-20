
- [General](#general)
- [Goal](#goal)
- [Diagram](#diagram)
  - [Distribution](#distribution)
  - [Flow](#flow)
- [Design](#design)
  - [Relative Strength](#relative-strength)
  - [Relatability](#relatability)
  - [Color](#color)
  - [Tweak](#tweak)
  - [Accessibility](#accessibility)
- [Chart Picking](#chart-picking)
- [Reference](#reference)


A visualization is a representation of the data, not the data itself.
It is there to be understood by an audience.

## General
Sketching is a critical part of the data visualization process:
- embracing failure
  - fail quickly
  - experiment easily
  - brainstorm efficiently
- picking the visual form (chart type, map, etc.)
- considering annotations
- envisioning animation/interactivity

ASK are the key ingredients of any successful visualization:
- A: accuracy
- S: story
- K: knowledge

3 focal points
- Know what your data is saying
- Know what your audience needs to hear
- Know what you really want to say


## Goal
- Help your audience
  - understand
  - remember
  - take action

| | Exploratory | Explanatory |
| --- | --- | --- |
| Purpose | Data Analysis Tool | Communications Device |
| Representation | dashboard of metrics/KPIs | annotations included |
| Filter | toggles | no digging required |
| Data | more with detail | less  |
| User | finds the insights | is shown the insights |


## Diagram
### Distribution
Look at __Distribution__ early:
1. Investigate consistency, skew
2. investigate count of data points with certain characteristics
3. investigate outliers

### Flow
When the point is really about how data flows from one thing to another - over time,
between categories, or in accumulation

- Waterfall Chart: the deconstructed Stacked Column Chart
- Sankey Diagram: Stacked Columns as two ends of the flow with connector lines in between



## Design

### Relative Strength
pre-attentive triggers on:
- value difference
  - position on a common scale
  - length of object
  - angle
  - area (particularly rectangles)
  - color (luminance / saturation)
- category differentiation
  - spatial region
  - color (hue)
  - motion
  - shape

### Relatability
- nature of the numbers
- the right metaphors
- understandable concepts
- recognizable visuals

### Color
- Adobe Color: https://color.adobe.com/
- color advice for cartography: https://colorbrewer2.org/
- Beautiful color palettes: https://www.colorpoint.io/
- Color tools for design systems: https://leonardocolor.io/
- Colors for data scientists: https://medialab.github.io/iwanthue/

### Tweak
- color
- label
- scale
- annotation
- title

### Accessibility
- use sufficient contrast
- consider color-blindness (no more red / green)
- consider screen reader (use alt text / caption)




## Chart Picking
Chart Suggestion:
![Chart Suggestion](<picture/Chart Suggestion.jpg>)

Visual Vocabulary:
![Visual Vocabulary](<picture/Visual Vocabulary.png>)

- Financial Times Visual Vocabulary: https://github.com/Financial-Times/chart-doctor/tree/main/visual-vocabulary
- Data Viz Project: https://datavizproject.com/
- Dataviz Inspiration: https://www.dataviz-inspiration.com/
- Weird but (sometimes) useful charts: https://xeno.graphics/


## Reference
- Learning Data Visualization: https://www.linkedin.com/learning/learning-data-visualization-15572314
- reMarkable: https://remarkable.com/
