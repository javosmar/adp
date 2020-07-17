A simple RPL network with UDP communication. This is a self-contained example:
it includes a DAG root (`udp-server.c`), intermediate DAG nodes 
(`udp-intermedio.c`) and a client node with a switch.
The button in the client switch turns the LEDs on the server node on and off.
This example runs without a border router -- this is a stand-alone RPL network.

The `.csc` file shows an example networks in the Cooja simulator,
for cooja motes.

