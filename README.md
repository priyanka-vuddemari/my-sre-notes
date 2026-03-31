# SRE Notes

## What is SRE?
Site Reliability Engineering (SRE) is a discipline that incorporates aspects of software engineering and applies them to infrastructure and operations problems. Originating at Google, SRE focuses on building and running large-scale, reliable systems. It treats operations as a software problem, emphasizing automation, monitoring, and engineering practices to ensure system reliability.

## Purpose and Reason for the SRE Team
The primary purpose of an SRE team is to ensure that services are reliable, scalable, and efficient while allowing development teams to move fast. SRE teams exist because traditional operations roles couldn't scale with the complexity and velocity of modern software development. They bridge the gap between development and operations by applying engineering principles to operational challenges, preventing outages, reducing toil, and enabling innovation without compromising reliability.

## Principles of SRE
1. **Reliability is a Feature**: Treat reliability as a quantifiable feature, not just an operational concern.
2. **Embrace Risk**: Accept that 100% uptime is impossible and focus on managing acceptable levels of risk.
3. **Eliminate Toil**: Automate repetitive tasks to free up time for engineering work.
4. **Monitoring and Observability**: Implement comprehensive monitoring to understand system behavior.
5. **Incident Response**: Learn from failures through blameless postmortems and continuous improvement.
6. **Service Level Objectives (SLOs)**: Define and measure reliability targets.

## Tenets of SRE
1. **Operations is a Software Problem**: Apply software engineering practices to operations.
2. **Share Ownership**: SREs and developers share responsibility for production systems.
3. **Reduce Toil**: Aim to spend no more than 50% of time on operational work.
4. **Monitoring**: Monitor everything that matters, alert on symptoms, not causes.
5. **Automation**: Automate everything possible to reduce human error and scale.
6. **Postmortems**: Conduct blameless postmortems for every incident.
7. **Capacity Planning**: Proactively plan for growth and failure scenarios.
8. **Gradual Change**: Implement changes gradually with rollback capabilities.

## SRE vs DevOps
While both SRE and DevOps aim to improve collaboration between development and operations, they differ in approach:

- **DevOps**: A cultural and process movement that emphasizes collaboration, automation, and continuous delivery. It's more about breaking down silos and improving the entire software delivery lifecycle.
- **SRE**: A specific implementation of DevOps principles, originating from Google. It focuses heavily on reliability engineering, risk management, and applying software engineering to operations. SRE is more prescriptive with concepts like SLOs, error budgets, and toil reduction.

SRE can be seen as a concrete way to implement DevOps, with more emphasis on quantitative approaches to reliability.

## What is SLA?
Service Level Agreement (SLA) is a contract between a service provider and its customers that defines the level of service expected. It specifies metrics like uptime, response time, and availability that the service must meet. SLAs are legally binding and often include penalties for non-compliance. For example, an SLA might guarantee 99.9% uptime for a web service.

## What is SLO?
Service Level Objective (SLO) is an internal target for service reliability. Unlike SLAs, SLOs are not customer-facing contracts but internal goals set by the SRE team. SLOs define what "good" service looks like in quantitative terms. For instance, an SLO might target 99.95% availability for a service over a rolling 28-day window.

## What is Risk?
In SRE context, risk refers to the probability and impact of service failures. It's the chance that a system will fail to meet its reliability objectives. Risk is measured in terms of potential downtime, data loss, or degraded performance. SREs quantify risk to make informed decisions about where to invest time and resources.

## How to Manage and Measure Risk
1. **Identify Risks**: Use techniques like Failure Mode and Effects Analysis (FMEA) to identify potential failure points.
2. **Quantify Risk**: Calculate risk using formulas like Risk = Probability × Impact.
3. **Prioritize**: Focus on high-risk, high-impact issues first.
4. **Mitigate**: Implement controls like redundancy, circuit breakers, and graceful degradation.
5. **Monitor**: Continuously track risk metrics and adjust as systems evolve.
6. **Balance**: Weigh risk against development velocity and business needs.

## What is Risk Tolerance?
Risk tolerance is the amount of risk an organization is willing to accept. It's the threshold beyond which the cost of additional reliability measures outweighs the benefits. Risk tolerance varies by service criticality - a core banking system might have very low risk tolerance, while a social media feature might have higher tolerance. It's expressed as acceptable levels of downtime or error rates.

## Error Budget
An error budget is the amount of unreliability that is acceptable for a service. It's calculated as 100% minus the SLO target. For example, if your SLO is 99.9% availability, your error budget is 0.1% (about 43 minutes of downtime per month). The error budget concept allows teams to innovate faster when reliability is good, and slow down when approaching the budget limit. It provides a quantitative way to balance reliability with feature development.