# dep-module-tester
Testing out dependency modules in mvn

## Need to build specific modules in aggregator

This project seeks to identify the technique in mvn that can effectively build a specific project (in an aggregator pom) and its dependencies without the other unnecessary dependencies.

### Setup
```
├── pom.xml
├── sibling-aggregator1
│   ├── cousin1
│   │   └── pom.xml
│   ├── cousin2
│   │   └── pom.xml
│   └── pom.xml
└── sibling-aggregator2
    ├── cousin3
    │   └── pom.xml
    ├── cousin4
    │   └── pom.xml
    └── pom.xml
```

### Assumption
cousin1 depends on cousin3

### Execution

To only build `cousin1` and its dependencies, run

```bash
mvn clean package -pl com.kilo:cousin1 -am
```

Do not use `amd` because it will prematurely build `cousin3`