# Tree Diagram (Mermaid)

```mermaid
flowchart TD
START --> A1_OPEN --> A1_D1
A1_D1 --> A1_Q1
A1_D1 --> A1_Q2
A1_Q1 --> A1_Q3 --> A1_R1 --> B1 --> A2_OPEN
A1_Q2 --> A1_Q4 --> A1_R2 --> B1B --> A2_OPEN
A2_OPEN --> A2_D1
A2_D1 --> A2_Q1
A2_D1 --> A2_Q2
A2_Q1 --> A2_Q3 --> A2_R1 --> B2 --> A3_OPEN
A2_Q2 --> A2_Q4 --> A2_R2 --> B2B --> A3_OPEN
A3_OPEN --> A3_D1
A3_D1 --> A3_Q1
A3_D1 --> A3_Q2
A3_Q1 --> A3_Q3 --> A3_R1 --> SUMMARY --> END
A3_Q2 --> A3_Q4 --> A3_R2 --> SUMMARY2 --> END2
```
