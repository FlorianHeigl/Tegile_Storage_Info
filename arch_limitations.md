

## Known or suspected limitations

Design Flaws
Hot Spare per Pool hardwired, auch bei Raidz2

Suboptimales vdev layout in vielen Configs

Schafft selten full stripe writes

u.U. Schlechte Performance wenn Volume parameter nicht genau passen, es gibt nicht so einen "alles wird zu 8K" Layer wie bei Pure

Weniger Compression algorithms als bei OpenZFS, und wird ohne HW offload gemacht Heute muesste man das neu designen und compression/dedup mit einer SmartNIC/DPU handlen

L2ARC RAM Usage Patches vermutlich nicht enthalten

Dedup RAM Usage Patches vermutlich nicht enthalten

Distributed Raid nicht portiert (d.h. schlechtere Raid6 Performance und ineffiziente Rebuilds)

Kein Boot-to-Ram

CPU Typ vermutlich nicht ideal fuer Low-Latency System (2680v3 vs. 2677v4 o.ae.). QPI Speed ist die gleiche, aber man sieht in DB Benchmarks unterschiede, zugunsten eben ca. 2677v4.

1 statt 2 pcie switch/bridge zwischen nodes, keine redundanz an der stelle

nur 1 nvdimm je node

vermutlich kein RDMA support / nutzung in nvdimm sync - es ging zwar ueber die PCIe Switches, aber mit viel OS hilfe.

Keine Skalierbarkeit > 2 Nodes Kein BIOS integrierter reinstall ala Tru64/VMS/Shared Root (das haette auch nur eine SD Karte sein koennen)

Limitierung auf 2 Pools, vermutlich nur aufgrund der NVDIMM Partitionierung

8GB NVDIMM anstatt 16/32GB

Das Chassis ist vermutlich ohne Input von jemand mit Midrange oder Highend Storage rausgesucht wurden. Nur 2 externe SAS Ports pro node... Bottleneck usw.

Grosse Performance Versprechen aber ausschliesslich langsamere read-optimized ssd verwendet - mit auswirkung auf die Latenz

Fake Active-Active
