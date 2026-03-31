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

## Service Level Agreement (SLA) 
Service Level Agreement (SLA) is a contract between a service provider and its customers that defines the level of service expected. It specifies metrics like uptime, response time, and availability that the service must meet. SLAs are legally binding and often include penalties for non-compliance. For example, an SLA might guarantee 99.9% uptime for a web service.

**Example:**
- If the service does not meet the SLO of 99.9% uptime, the service provider will provide a credit to the client.
  
## Service Levele Object (SLO)?
Service Level Objective (SLO) is an internal target for service reliability. Unlike SLAs, SLOs are not customer-facing contracts but internal goals set by the SRE team. SLOs define what "good" service looks like in quantitative terms. For instance, an SLO might target 99.95% availability for a service over a rolling 28-day window.

**Example:**
- Our SLO for response time is 99.9% of requests served within 200ms.
  
## Service Level Indicator (SLI)
An SLI is a metric that measures the performance of a service based on a specific aspect that is critical to the user experience. For example, if you are providing a web service, an SLI might measure the response time of that service.

**Example:**
- Percentage of successful responses (HTTP 200) over total requests in a given timeframe.

## Understanding SLI, SLO, and SLA - Simple Analogies

### Health & Fitness Journey Analogy

Think of these concepts as a Health & Fitness Journey:

- **SLI (Indicator)**: This is your scale or your fitness tracker. It is the raw data that tells you what is actually happening right now (e.g., your weight is 80kg, or you ran 5km today).
- **SLO (Objective)**: This is your goal. It is the specific target you want to hit based on your indicators (e.g., "I want to weigh 75kg by next month" or "I want to run at least 5km every day").
- **SLA (Agreement)**: This is the contract. It is the promise you make to someone else, usually with a penalty if you fail (e.g., "If I don't lose 5kg this month, I will pay my personal trainer a ₹500 fine").

### Pizza Delivery Analogy

Another popular way to look at it is through a pizza shop:

| Term | Simple Definition | Example |
|------|-----------------|---------|
| SLI | The Measurement | The actual time it took for the driver to reach your door (e.g., 28 minutes). |
| SLO | The Internal Target | The shop's internal goal to keep customers happy (e.g., "We aim to deliver 95% of pizzas within 30 minutes"). |
| SLA | The Customer Promise | The public guarantee: "Delivered in 30 minutes or it's free!".

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


### To understand the concept of an Error Budget, we can use the analogy of a data plan for your mobile phone. Here’s how it breaks down:

1. **The Allowance**: Just like your mobile phone plan has a certain limit of data you can use each month, an Error Budget defines how much error or downtime is acceptable within a specific timeframe. This allowance is determined by the agreed-upon service level objectives (SLOs).

2. **Spending it**: When you access the internet, you are using your allotted data. Similarly, when users experience issues or downtime, they are “spending” the Error Budget. Keeping track of this spending is essential to ensure you do not exceed your limits.

3. **Taking Risks**: In both scenarios, you might intentionally choose to use more data (like streaming video) at the risk of going over your limit. In the context of Error Budgets, teams may decide to take risks with certain features or deployments that could impact uptime, knowing that there’s a buffer.

4. **The Limit**: Every data plan has a cap. If you exceed your data allowance, you might incur extra charges or experience throttled speeds. Similarly, if you exceed your Error Budget, it can lead to severe consequences, such as degraded service quality and customer dissatisfaction.

5. **The Consequence**: Exceeding data limits results in either financial penalties or slower service. For Error Budgets, exceeding the agreed level of error can lead to serious consequences for your service, necessitating immediate corrective actions to improve reliability and potentially harming your reputation.

Using the Data Plan analogy to explain Error Budgets helps stakeholders understand the importance of balancing risk and reliability. By providing a relatable framework, teams can grasp the necessity of monitoring error rates actively and making informed decisions about deployments. This ultimately leads to better resource management, improved customer satisfaction, and a more resilient system overall.
