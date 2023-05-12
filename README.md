**Modify FIle names as required along with number of days for certificates to be valid**


Create KEY for ca

	openssl genrsa -des3 -out ca.key 2048

Create CERT for CA
	
	openssl req -new -x509 -days 1826 -key ca.key -out ca.crt
	
Create SERVER KEY

	openssl genrsa -out server.key 2048
	
Create SERVER CSR

	openssl req -new -out server.csr -key server.key
	
Sign SERVER CERT with CA
	
	openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt -days 360
