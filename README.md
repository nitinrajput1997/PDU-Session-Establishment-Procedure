# PDU-Session-Establishment-Procedure

Whenever a new PDU Session is created, then this procedure is employed. Alternatively, when a PDU Session is handed over from non-3GPP access like Wi-Fi, at that time the PDU Session establishment procedure is used. Typically this procedure is always initiated by the device. But if the network would like to trigger it, then it can send the trigger message to a device. Following that message, the device will initiate the establishment procedure.

**PDU Session Establishment Procedure Call Flow**

In the first step, the device sends the PDU Session establishment request to the radio access network, which further forwards it to the AMF. This request contains the information like which data network the device is requesting a PDU Session towards, what type of session it was looking for, is it an IP based session or Ethernet type session or is an unstructured session. There is one more necessary piece of information that is this a new PDU Session or is it a handover.

In the case of a new PDU Session, the AMF will see what is the kind of session that the device has requested, and what data network it was trying to connect with. For example, if a device is trying to connect to IMS, then the AMF will select the appropriate SMF to do the session handling. On the other hand, if the connectivity is towards the internet then the AMF will select the corresponding SMF for doing the session management. 

In a case when a device is requesting a session handover then it is not a new PDU Session. So then the AMF will look into the device context and that context will already be associated with the particular SMF. So it can contact the corresponding SMF in that case.

Now the AMF contacts the SMF for creating the session management context and in addition, it contacts the UDM to get the necessary subscription data and also subscribe to further updates of that subscription data.

When the SMF agrees with the session management context creation, it will provide the corresponding positive acknowledgement as the response. If any authorization is necessary it was taken care of in the next step. 

Now after authorization, the SMF selects the appropriate PCF and creates a policy session so that it can get the necessary PCC rules from the PCF. And also it selects the appropriate UPF to connect to the correct data network and creates the connectivity with the corresponding UPF.

Now in the next step, the SMF sends the accept message toward the device together with the information related to the quality of service and also tunnel information between the gNodeB and UPF. And this information is sent via AMF. 

Then AMF forward this to the radio access network. The quality of service and tunnelling information has reached the radio access network. Then the radio access network creates the connectivity to the device. And request back to the AMF with the tunnelling information on the end-point of the radio access network. 

This means that all the necessary setup has now been done for sending the Uplink-Data from the device towards the 5G system. So the first uplink data can now be sent. In the next step, the AMF has previously received the RAN ends tunnel information from the RAN. Now it forwards this to the SMF and the SMF forwards this to the UPF. So that the UPF will know, what is the tunnel endpoint in the RAN-end. 

So it establishes the connectivity from the UPF to the RAN. Now the GTP tunnel is complete, which means that now the UPF can forward the first Downlink-Data from the data network toward the device. So at this point, the data network connection is complete. Now both uplink and downlink data communication is successful. The AMF can go and register itself with the UDM, this is the SMF corresponding to the PDU session that was currently created.
