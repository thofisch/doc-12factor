# API First

Regardless of the type of application, the ultimate goal might very well be to have that application be a participant in an ecosystem of services.

Even if, at the outset, the service is not a part of a larger ecosystem, the discipline of starting development at the API level still pays enough dividends to make it worth the effort.

When building cloud-native applications, chances are another team in the organization starts building services relying on your code. Soon multiple teams are building services with horizontal dependencies that are all on a different release cadence.

To avoid integration failures, API first gives teams the ability to work against each other’s public contracts without interfering with internal development processes.

If we treat and develop all applications as [backing services](/backing-services), and designed them API-first; the system will be free to grow, adapt to new load and demand, and accommodate new consumers without having to re-architect yet another closed system.

{>>Link to our in-depth API First guidelines<<}