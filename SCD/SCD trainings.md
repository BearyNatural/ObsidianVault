S3 overview:
S3 lifecycle management  
define/configure let of rules for what action to perform2 actions:  
transition  
deletecan move from standard to glacier but not glacier to standard  
after deletion customer is not charged. it may take upto 2 days to delete. but customer is not chargedin transition, customer is charged for the destionation classfilters:  
key prefix  
object tags no charge for deleting object  
early deletion fee if customer deletes earlier than the defined rules. glacier has min 90 days duration and galcier archive has min 180 dayscli upload creates multiple parts  
if network issues, 4 uploaded, 6 not uploaded and stored in memory and customer is chargeddelete markers are called expired delete markers.. a file that does not have previously delete markers. can set up lifecycle rules for thiss3 lense to see what's incomplete so we delete andstatic website hosting:  
does not support HTTPS. If need https then use cloudfrontmust be public bucket, object must have public access

- bucket policies - EPARC
	- Effect: allow or deny
	- Principal: the entity that is allowed or denied access
	- Action: Type of access that is allowed or denied
	- Resource: The amazon resource the action will act on
	- Condition: The conditions that are valid under the access defined

storage gateway family
- s3 file gateway: file storage backed by s33
- volume gateway: backed by ebs shapshots
- tape gateway: virtual tapes that uses amazon glacier
- fsx file gateway: file storage backed by fsx for windows

internal error during today's lab, need to go to vpc endpoints and delete storage gateway interface that was created in the private - will be recreated later??
go back to storage gateway and recreate as per instructions

imap & pop3 allow you to receive emails 
- pop3 assumes email accessed only from one application
- pop3 downloads them from server to local and deletes them from server
- imap allows simultaneous access by multiple clients
smtp allows you to send messages
