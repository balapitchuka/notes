## Kafka basics:

1. Topic : A Particular stream of data.
   - A topic is identified by its name.
   - topics are split into partitions.
   - Each message within a partition gets an incremental id, called offset.
   
 Reallife Example:  **truck_gps***
 > Say you have a fleet of trucks, each truck reports itf GPS to kafka.<p>
 We can here have a kafka topic trucks_gps, that contains the position of all the trucks.<p>
 Each truck will send a message say every 20 seconds indicating its position. Each message will contain the truckid and truck    position(latitude and longitude)

 
   
