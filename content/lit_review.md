## Related work
{:#related_work}

SQUIN [](cite:cites Hartig2013) propose an iterator architecture where each iterator is responsible for a triple pattern.
During the execution of iterator first get the solution map of the previous iterator, 
than it tries to find matching members in the local dataset finally it extends the internal data source by deferring the link that respects the
reachability criteria. With this architecture it is possible to have non-blocking operators and to use heuristic based query planning.

SHIH [](cite:cites Ladwig2011) propose a relatively similar architecture, but they provide a cost model strategy to effectute the query plan, 
but it has to be noted that their is no description for getting the selectivitity of the join operation to order them.

The next work from the same first author [](cite:cites Hartig2016) expend on this iterator architecture.
The focus of the architecture this time is to enable adaptative query planning by taking as an inspiration Eddy operator design.
The execution of the query is divided in three operators; <q>Data Retrievals</q> (DR), <q>Triple Patterns Operators</q> (TPO) and <q>Dispatcher</q> (DO)
where each operation is perform on a different thread and comunicate togheter using a bus.
DR, is responsible for performing the traversal to retrieve the data from 
the web to the internal query engine data source. 
TPO who is responsible for finding matching triple patterns received from DR, sand build results or intermediaries from other TOP throught the dispatcher.
DO, for its part, receive and send intermediary results from TOP and also send results to the end user.

Miranker et Al. [](cite Miranker2012) propose to use an architecture using a Rete-Match network. 
It consist of having a module that does the derefencing of URI from the web, to store than in a local triple store and to queue them to
enter an Rete-Match network with rules equivalent to the SPARQL algebra to create intermediary results that are store in alpha memories and beta memories and
to forward URI to dereference in a queue and complete results to the user.