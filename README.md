# drill

Installation & start up:

wget http://shinyfeather.com/drill/drill-1.6.0/apache-drill-1.6.0.tar.gz
mkdir /opt/drill
cp apache-drill-1.6.0.tar.gz /opt/drill
cd /opt/drill/
tar -xvzf apache-drill-1.6.0.tar.gz 
cd apache-drill-1.6.0/bin


sample conf: 
conf/drill-override.conf
drill.exec: {
  cluster-id: "drillbits1",
  zk.connect: "localhost:2181"
}

embedded:
  ./drill-embedded (!quit to end)
Cluster mode (needs zookeeper running):
  ./drillbit.sh start
  
To check if running on default port:
  netstat -tulpn | grep :8047
