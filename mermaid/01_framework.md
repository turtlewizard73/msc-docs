## color codes:
- white: #fff
https://mermaid.js.org/syntax/flowchart.html
https://mermaid.js.org/config/theming.html#flowchart-variables
packages/button
├── lib
│   ├── button.d.ts
│   ├── index.js
│   └── index.js.map
├── package.json
│   └── index.ts
└── tsconfig.json

```mermaid
flowchart TD
    roslogoA@{ img: "https://www.freshconsulting.com/wp-content/uploads/2022/07/ROS-2_logo.png", label: "Image Label", pos: "t", w: 60, h: 60, constraint: "off" }
```

```mermaid
%%{
    init: {
        'securityLevel': 'loose',
        'theme': 'base',
        'themeVariables': {
            'darkMode':'false',
            'background':'#fff',
            'primaryColor':'#1e5067',
            'primaryBorderColor':'#1e5067',
            'primaryTextColor': '#fff',
            'secondaryColor':'#6BB6C7',
            'tertiaryColor':'#fff',
            'tertiaryBorderColor':'#000000',
            'clusterBkg':'#159ab7'
        }
    }
}%%

flowchart TD
    subgraph os ["OS"]
        direction LR

        display@{ shape: curv-trap, label: "Display" }

        subgraph docker ["Docker"]
            style docker stroke:#fff,stroke-width:3px,color:#fff,stroke-dasharray: 5 5
            launch(["ros2 launch"])
            ros["ROS2"]
            python(["python3"])
            gazebo(["Gazebo"])
            rviz(["RViz"])
            bo["Benchmark & Optimizer"]

            launch ==> ros
            launch --> gazebo
            launch --> rviz

            python ==> bo
        end

        gazebo --> display
        rviz --> display

    end

```