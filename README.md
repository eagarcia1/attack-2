# attack-2

sequenceDiagram
    participant Attacker
    participant BotNet
    participant WebServer
    participant Firewall
    
    %% Attacker initiates the command
    Attacker->>BotNet: Send attack command
    
    %% BotNet propagates the attack signal amongst bots
    loop Propagation phase
        BotNet-)BotNet: Spread command to bots
    end
    Note over BotNet: Bots activated for attack

    %% BotNet initiates the attack on the WebServer
    BotNet->>WebServer: Begin flood of requests

    %% WebServer communicates anomaly to Firewall
    WebServer-->>Firewall: Detect abnormal traffic

    %% Firewall acts based on traffic patterns
    alt Traffic exceeds threshold
        Firewall->>Firewall: Perform traffic analysis
        Firewall->>Firewall: Blacklist offending IPs
        Firewall-->WebServer: Allow safe traffic
    else Traffic is within normal parameters
        WebServer->>BotNet: Respond to legitimate requests
    end

    %% Mitigation in progress
    Note over Firewall, WebServer: Traffic management ongoing
