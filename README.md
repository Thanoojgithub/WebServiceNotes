# WebServiceNotes
webService notes


Bottom-Up ::

i.e. Contract-last. There are the following reasons for preferring a Bottom-Up development style.

Code first
Initial stage very easy to develop.
Maintenance is very very hard.

Top-Down ::

i.e. contract-first. There are the following reasons for preferring a Top-Down development style.

1. Fragility The contract-last development style results in your web service contract (WSDL and your XSD) being generated from your Java contract (usually an interface). If you are using this approach, you will have no guarantee that the contract stays constant over time. Each time you change your Java code and redeploy it, there might be subsequent changes to the web service contract. Aditionally, not all SOAP stacks generate the same web service contract from a Java contract. This means changing your current SOAP stack for a different one (for whatever reason), might also change your web service contract. When a web service contract changes, users of the contract will have to be instructed to obtain the new contract and potentially change their code to accommodate for any changes in the contract. In order for a contract to be useful, it must remain constant for as long as possible. If a contract changes, you will have to contact all of the users of your service, and instruct them to get the new version of the contract.

2. Performance When Java is automatically transformed into XML, there is no way to be sure as to what is sent across the wire. An object might reference another object, which refers to another, etc. In the end, half of the objects on the heap in your virtual machine might be converted into XML, which will result in slow response times. When using contract-first, you explicitly describe what XML is sent where, thus making sure that it is exactly what you want.

3. Reusability Defining your schema in a separate file allows you to reuse that file in different scenarios.

4. Versioning Even though a contract must remain constant for as long as possible, they do need to be changed sometimes. In Java, this typically results in a new Java interface, such as AirlineService2, and a (new) implementation of that interface. Of course, the old service must be kept around, because there might be clients who have not migrated yet. If using contract-first, we can have a looser coupling between contract and implementation. Such a looser coupling allows us to implement both versions of the contract in one class. We could, for instance, use an XSLT stylesheet to convert any "old-style" messages to the "new-style" messages.


Top-down means you start with a WSDL and then create all the necessary scaffolding in Java all the way down.

Bottom-up means you start with a Java method, and generate the WSDL from it.

SOAP means that the URL is the same for all invocations, and only the parameters to the Java method differs. REST means that the URL reflects the operation to be done.
