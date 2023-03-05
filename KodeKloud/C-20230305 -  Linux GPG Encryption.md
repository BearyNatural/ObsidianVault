We have confidential data that needs to be transferred to a remote location, so we need to encrypt that data.We also need to decrypt data we received from a remote location in order to understand its content.
On `storage server` in `Stratos Datacenter` we have private and public keys stored `/home/*_key.asc`. Use those keys to perform the following actions.
-   Encrypt `/home/encrypt_me.txt` to `/home/encrypted_me.asc`.    
-   Decrypt `/home/decrypt_me.asc` to `/home/decrypted_me.txt`. (Passphrase for decryption and encryption is `kodekloud`).

ststor01
172.16.238.15
ststor01.stratos.xfusioncorp.com
natasha
Bl@kW
Nautilus Storage Server

%% ssh to ststor01  %% Bl@kW
ssh natasha@ststor01
sudo -i

%% encrypt data research %% https://www.howtogeek.com/427982/how-to-encrypt-and-decrypt-files-with-gpg-on-linux/
gpg --help
	-e --encrypt
	-d --decrypt

%%setup %%
cd /home
gpg --import public_key.asc
gpg --import private_key.asc
gpg --list-keys [
/root/.gnupg/pubring.gpg
------------------------
pub   2048R/CCE3AF51 2020-01-19
uid                  kodekloud <kodekloud@kodekloud.com>
sub   2048R/865C070D 2020-01-19]
gpg --list-secret-keys [
/root/.gnupg/secring.gpg
------------------------]

%% encrypt/decrypt data %%
gpg --encrypt -r kodekloud@kodekloud.com --armor < encrypt_me.txt -o encrypted_me.asc [y]
gpg --decrypt decrypt_me.asc > decrypted_me.txt [kodekloud]

%% confirm job done %%
ll [-rw-r--r-- 1 root    root      80 Mar  4 21:52 decrypted_me.txt -rw-r--r-- 1 root    root     669 Mar  4 21:52 encrypted_me.asc]
cat decrypted_me.txt
cat encrypted_me.asc
exit


