# Database

## Types
### Relational and non-relational database
| | Relational database | Non-relational database |
|---|---|---|
| Alias | SQL database | NoSQL database |
| Features | <li>Rows and columns in a series of tables | <li>Schema free |
| Query Language | SQL | |
| Sub-types | | <li>Document<li>Wide-column<li>Key-value<li>Graph<li>Object<li>Tuple |

## Techniques
### Replication
| | Master-slave | Master-master |
|---|---|---|
| Architecture | ![C9ioGtn](https://user-images.githubusercontent.com/8989447/116644854-b334b680-a931-11eb-9ff5-60f57652b09d.png) | ![krAHLGg](https://user-images.githubusercontent.com/8989447/116644889-cc3d6780-a931-11eb-956d-c6eebf2f218f.png) |
| Alias | Single-leader | Multi-leader |
| Write operations | Master only  | Masters |
| Read operations | Master and slaves | Masters |
| Failure handling | <li>If the master is down, one of the slave will be promoted to be a new master. | <li>If one master is down, other masters can still handle reads and writes. |

### Partitioning
- Types
   - Horizontal partitioning (Sharding): Split data by row.
   - Vertical partitioning: Split data by column.

#### Sharding
- Strategies
  | | By key range | By hash of key |
  |---|---|---|
  | Example | ![ddia_0602](https://user-images.githubusercontent.com/8989447/116647540-09a4f380-a938-11eb-9621-eeeff91e442c.png) | ![ddia_0603](https://user-images.githubusercontent.com/8989447/116647659-525cac80-a938-11eb-847f-c44bfec9f68a.png) |
  | Concept | Assign a range of keys to each partition. | Assign a range of hashes to each partition. |
  | Pros | <ul><li>Range queries are easy.</ul> | <ul><li>Keys distributing is fair among the partitions.</ul> |
  | Cons | <ul><li>Certain access patterns can lead to hot spots (A partition with disproportionately high load).</ul> | <ul><li>Lose the ability to do efficient range queries.</ul> |

### Federation