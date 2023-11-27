## Introduction
{:#introduction}
 
The concept of data vaults has emerged in an effort to give more control to the users over the storage and the access to their data; it is encapsulated in a bigger concept called data sovereignty [](cite:cites Verstraete2022).
Combined with linked data it creates the basis for more interoperable applications thus
giving also more choice of providers of services [](cite:cites Verstraete2022).

Due to the highly decentralized nature of data vault environments, Link Traversal Query Processing (LTQP) is the preferred query paradigm [](cite:cites Taelman2023). LTQP consists of executing a query over an internal data store while recursively dereferencing links following a lookup policy to add more data into the internal data store [](cite:cites Hartig).
LTQP has been studied by multiple researchers ( for example those authors [](cite:cites Hartig2016, Ladwig2011, Miranker2012)) in the context of the **open web**.
The current consensus is that the bottleneck for fast query execution is the number of HTTP requests [](cite:cites Hartig2016).


Taelman et al. [](cite:cites Taelman2023) in their work have demonstrated that 
the query plan has a significative (more than twice) impact on the query execution time in the context of networks of data vaults or more generally in <q>Decentralized Environment[s] with structural assumptions</q>[](cite:cites Taelman2023).
In this paper, we do not try to invalidate the experience realized by Taelman et al. [](cite:cites Taelman2023)
but we investigate if the architecture of the query engine had an impact on that conclusion.
Indeed, Hartig et al. [](cite:cites Hartig2016) have proposed to execute the dereferencing of
links and the execution of the query in parallel (multiple threads) whereas in the contribution of Taelman et al. [](cite:cites Taelman2023)
the engine executes those operation in concurrence (asynchronously in one thread).
This choice of architecture could have the consequence of accumulating significantly more surplus execution time due to a non-optimal query plan compared to a parallel architecture particularly given a large number of data sources and of triple to process. 

More concretely our research question is the following.
Is the suraccumulation of idle time caused by the fetching of online documents (HTTP requests time) in one execution thread the cause
of the statistical difference of query execution time between the ideal query plan (from an oracle) and the concrete implementation of the query engine in the context of <q>Decentralized Environment[s] with structural assumptions</q>[](cite:cites Taelman2023)?
