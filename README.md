# salt

---

Images: (Leap 42.1 w/ Salt packages)


from Google Drive : https://drive.google.com/open?id=0B3R6ugJrl9iOa2dSTU92WmxMSWc

vanity URL : https://goo.gl/CLG4Dy

---

Using KVM, import these images to running state

---

On Master:
fix hostname via YaST -> salt.suse
systemctl enable salt-master
systemctl start salt-master
salt-key
vi /etc/salt/minion
	master: localhost
systemctl enable salt-minion
systemctl start salt-minion
salt-key
salt-key -a salt.suse
salt \* test.ping
salt \* test.version

On Minion:
fix hostname via YaST -> minion
vi /etc/salt/minion
	master: <IPofMaster>
systemctl enable salt-minion

then back to master and accept key for new minion, and 
salt \* test.ping
salt \* test.version
salt minion* grains.items

Use Case:

Fix NTP

