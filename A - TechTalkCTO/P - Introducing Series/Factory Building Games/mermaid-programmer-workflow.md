```mermaid
%% imgs is generated via : https://mermaid.live/ %%
graph TD
    %% This is a "workaround" block to provide a title like header
    title[<font size=19>Typical Programmer Workflow</font>\nStart to end of task, happens across a week to a month]
    title---A1
    style title fill:#FFF,stroke:#FFF;
    linkStyle 0 stroke:#FFF,stroke-width:0;

    subgraph SG1 [Development Process]
        C1(("🙂 Start of task"))
        C1 --> D1

        D1("🤔 Choose among various tools\nto achieve a task")
        D2("🤔 Plan and design a new subsytem\nto meet requirements")
        D1 --> D2

        E1{{"🤓 code the prototype"}}
        D2 --> E1

        E2("😬 Self test the prototype")
        E1 --> E2

        G1("🥳 Found good working prototype")
        G2{{"🤓 Refine the code & make it production ready"}}
        E2 --> G1
        G1 --> G2

        G3("😬 Test with user groups / teamates")
        G2 --> G3

        H1("😬 Deploy into production !!!")
        G3 --> H1

        J1("🥳 Requirements are met")
        H1 --> J1
        
        X1(("🥳 End of task "))
        J1 --> X1

        ZFAIL1(("😭 Failure"))
        E1 -.-> ZFAIL1
        E2 -.-> ZFAIL1
        G3 -.->ZFAIL1
        H1 -.->ZFAIL1
        ZFAIL1 -.back to the drawing board.-> D1
        ZFAIL1 -.iterate on the code.->E1
        
        ZSAD1("😭 User is unhappy, \nrequirements are changed")
        ZSAD1 -.-> ZFAIL1
        J1 -.-> ZSAD1

        %% Red failures
        style ZFAIL1 fill:#e0b7b4
        style ZSAD1 fill:#e0b7b4

        %% organge stressors
        style G3 fill:#e0d1b4
        style H1 fill:#e0d1b4
        style E2 fill:#e0d1b4

        %% Green happy stuff
        style C1 fill:#b6e0b4
        style G1 fill:#b6e0b4
        style J1 fill:#b6e0b4
        style X1 fill:#b6e0b4
    end

    subgraph SG2 [Misc work / Distractions]
        Z1["😬 Endless meetings /\nSystem error & downtime /\nCustomer complains /\nOther work duties"]

        %% organge stressors
        style Z1 fill:#e0d1b4
    end

    subgraph SG3 [Project Planning \w your project manager]
        A1(Get new user requirements)
        A2(Found a new way to improve existing process)
        A3(Work on technical debt)
        A1 --> B1
        A2 --> B1
        A3 --> B1
        B1[Discussing, planning, and negotiating what to be done]
    end
    B1 --> C1
    B1 -.-> Z1
```