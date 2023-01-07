Copyright chain

```
graph TD
    subgraph "Works (artwork, content, etc)"
        BY["Under Public Domain / \nCreative Commons, \nwith attribution"]
        NC["Under Creative Commons, \nwith no commercial use restriction"]
        LI["Privately licensed artworks"]
    end
    subgraph "Dataset"
        C_DATA["Commercial use\nfriendly dataset"]
        NC_DATA["Non-Commercial use\n dataset"]
        LI_DATA["Privately licensed dataset"]

        BY-.collection.->C_DATA
        NC-.collection.->NC_DATA
        C_DATA-.can be merged in.->NC_DATA
        LI-.collection.->LI_DATA
    end
    subgraph "AI Model"
        C_AI["Commercial use\nfriendly AI model"]
        NC_AI["Non-Commercial use\n AI model"]
        LI_AI["Privately licensed\nAI model"]

        C_DATA-.training.->C_AI
        NC_DATA-.training.->NC_AI

        LI_DATA-.trained OR \nfinetuned with \ncommercial use friendly\nAI model.->LI_AI
    end
```

Input and output copyright mapping

| Input Copyright                              | AI model (with attribution)                                                                                                                                                   | AI model (with no commercial use restriction)                                                                                                                                                         | Custom licensed AI model                                                                                                                                                                                       |
|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Copyright protected / All rights reserved    | Prohibited, unless under "fair use"                                                                                                                                           | Prohibited, unless under "fair use"                                                                                                                                                                   | Prohibited, unless under "fair use"                                                                                                                                                                            |
| Creative Commons No Derivatives              | Prohibited, unless under "fair use"                                                                                                                                           | Prohibited, unless under "fair use"                                                                                                                                                                   | Prohibited, unless under "fair use"                                                                                                                                                                            |
| Creative Commons with Share Alike / Copyleft | Complicated (find a lawyer)                                                                                                                                                   | Complicated (find a lawyer)                                                                                                                                                                           | Complicated (find a lawyer)                                                                                                                                                                                    |
| Creative Commons with Attribution            | Attributed to  - the AI model - the human operator - the original input  Human Operator - Owns rights to use / commercialize - As long as it maintains attribution            | Attributed to  - the AI model - the human operator - the original input  Human Operator - Owns rights to use - As long as it maintains attribution - As long as its not for commercial use            | Attributed to  - the AI model - the human operator - the original input  Human Operator - Owns rights to use - As long as it maintains attribution - As long as it follows the custom license terms            |
| Public Domain / No input                     | Attributed to  - the AI model - the human operator - (optional) the original input  Human Operator - Owns rights to use / commercialize - As long as it maintains attribution | Attributed to  - the AI model - the human operator - (optional) the original input  Human Operator - Owns rights to use - As long as it maintains attribution - As long as its not for commercial use | Attributed to  - the AI model - the human operator - (optional) the original input  Human Operator - Owns rights to use - As long as it maintains attribution - As long as it follows the custom license terms |

Transformative use cases

| Input Copyright                              | Output is factual Extraction / Labeling                                                                             | Output has minor Enhancment / is Non Transformative                                                                                                                                                   |
|----------------------------------------------|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Copyright protected / All rights reserved    | Prohibited, unless under "fair use"                                                                                 | Prohibited, unless under "fair use"                                                                                                                                                                   |
| Creative Commons No Derivatives              | Prohibited, unless under "fair use"                                                                                 | Prohibited, unless under "fair use"                                                                                                                                                                   |
| Creative Commons with Share Alike / Copyleft | Complicated (find a lawyer)                                                                                         | Complicated (find a lawyer)                                                                                                                                                                           |
| Creative Commons with Attribution            | Attributed to  - the human operator  Human Operator - Owns rights to use / commercialize - Owns rights to licensing | Attributed to  - the AI model - the human operator - the original input  Human Operator - Owns rights to use - As long as it maintains attribution - As long as its not for commercial use            |
| Public Domain                                | Attributed to  - the human operator  Human Operator - Owns rights to use / commercialize - Owns rights to licensing | Attributed to  - the AI model - the human operator - (optional) the original input  Human Operator - Owns rights to use - As long as it maintains attribution - As long as its not for commercial use |