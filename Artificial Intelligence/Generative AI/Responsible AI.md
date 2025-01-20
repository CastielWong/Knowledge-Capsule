
- [Security, Governance \& Compliance](#security-governance--compliance)
- [Responsible Datasets](#responsible-datasets)
- [Interpretability vs Explainability](#interpretability-vs-explainability)

Core Dimension:
- Fairness: impartial and just treatment without discrimination
- Explainability: the ability to understand how a model arrives at a prediction
- Robustness
- Privacy and Security
- Veracity and Robustness
- Governance
- Transparency
- Safety
- Controllability


## Security, Governance & Compliance
- Security: ensure that confidentiality, integrity, and availability are maintained
for organizational data and information assets and infrastructure
- Governance: ensure that an organization can add value and manage risk in the
operation of business
- Compliance: ensure normative adherence to requirements across the functions of
an organization

Strategic Guidance:
1. Data Protection
   - data at rest
   - data in transit
2. Identity and Access Management
3. Application Protection
4. Network and Edge Protection
5. Infrastructure Protection
6. Threat Detection and Incident Response
7. Policies, Procedures, and Awareness

The [Generative AI Security Scoping Matrix](https://aws.amazon.com/blogs/security/securing-generative-ai-an-introduction-to-the-generative-ai-security-scoping-matrix/) is a framework used to classify generative AI use cases, which determines the level of ownership required for a use case and to prioritize security concerns.


## Responsible Datasets
- inclusivity: representing diverse populations, perspectives, and experiences
in training data
- diversity: incorporating a wide range of attributes, features, and variables
to avoid bias
- balanced datasets: ensuring equal representation of different groups and
avoiding skewed distributions
- privacy protection: safeguarding sensitive information and adhering to data
protection regulations
- consent and transparency: obtaining informed consent from data subjects and
providing clear information about data usage
- regular audits: conducting periodic reviews of datasets to identify and
address potential issues or biases


## Interpretability vs Explainability
Interpretability: how the inner mechanisms of the model impact the output
- more transparent
- deep level understanding of internal mechanics
- use interpretable __algorithms__, like Linear Algebra
- performance and security tradeoffs

Explainability: observing outputs relative to certain inputs for explanation
- less transparent
- high-level understanding (via the output instead of the model itself)
- model agnostic (black-box) approach
