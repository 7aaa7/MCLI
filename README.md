### DEMO  

    -  Web
        - <TODO>  
    -  CLI
        - Machine
            - graph <[server_regex]>([server modifiers]) <[metric_regex]>[(metric modifiers)] [duration] [type] [style] [size] 
        - Type
            - graph <[type_regex]>([type modifiers]) <[metric_regex]>[(metric modifiers)] [duration] [type] [style] [size] 
    
====

new ganglia interface
* Why a new interface ?
    - To allow more options for graphing
    -  TO create different graph types
    - To integrate alerting framework
    - Creating a API model for integration with other Applications
    - To easily create arbiruartary aggregate graphs for comparison

* How do we group the graphs ?
* A graph signifies a single metric historic pattern.
    - Multiple metrics can be graphed in a single graph if it matches the following cretiria
        - Different metrics but for same server grouped by "Metrics Group"
        - Same metric with different servers grouped by "Metrics Group"

* Grouping via Metrics group if multiple metrics 

# ganglia api model . 
APIs : 

    REQUEST METHOD : GET 
    1. List of Clusters given a grid name. 
        -  URL : list=clusters&grid="grid_name"
    3. List of Servers given list of cluster names. 
        -  URL : list=servers&cluster="list of cluster"
    3. List of metrics given a (list of/single servername.
        -  URL : list=metrics&server="list of servers"
    4. List of servers given a list of metrics.
        -   URL : list=servers&metric="list of metrics"
    5. List of metrics given a cluster name. 
        -  URL : list=metrics&cluster="cluster"
    6. Find the cluster given a servername 
        - : yet to implemented 
    7. List of all clusters 
        -    URL: list=clusters
    8. List of all servers 
        -    URL: list=servers
    9. List of all metrics 
        -    URL: list=metrics
    10. List of metrics group 
        -    URL: list=metrics_grp 
    11. List of metics belonging to a particular array/scalar value of metrics group 
        -    URL: list=metrics&metrics_grp="list of metrics group"


* Example Usage: 
    * To get list of all servers having "proc_run" as metric
        - http://<DOMAIN>/api/webservice.php?list=servers&metrics=proc_run
    * To get list of all metrics deployed 
        - http://<DOMAIN>/api/webservice.php?list=metrics
    * To get list of all metrics deployed for a particular server 
        - http://DOMAIN/api/webservice.php?list=metrics&servers=bll-us1


* RESPONSE :
    > default serialized reponse is JSON , you can change the response type to xml via appending "&method=xml" in the URI 
    > Example : 
    >    list=metrics&cluster="cluster"&method=xml


[2012-First-BetaVersion-Screenshot](https://github.com/7aaa7/MCLI/blob/master/screenshots/screenshot1.jpeg)

