# What Is Encryption?

  1. At its most basic level, encryption scrambles information so that only those people with the right decoder key can unscramble it. 

  2. You can encrypt all kinds of data. Phone numbers, dates, names, text files, images, you name it. If it’s recorded digitally, you can encrypt it.

    * Shield Platform Encryption encrypts data at rest, meaning that we encrypt it when it’s being stored within Salesforce.

# Should I Encrypt My Data?

  1. There are many factors to consider before deciding if you should encrypt your data at rest. 

    * Most companies and organizations are subject to some kind of regulation when keeping customer data secure. 

    * Also, contractual obligations and internal compliance policies often emphasize protecting client and customer data. 

    * While most data protection regulations don't require that businesses encrypt data at rest, most mention encryption as another access control tool for securing data at rest.

# What Are Keys and Secrets?

  1. The basis of encryption is scrambling and unscrambling. Keys do the scrambling and unscrambling, and secrets keep your keys safe and working properly.

  2. A key is a string of bits that scramble and unscramble data. Just like a physical key can lock and unlock a door, encryption keys lock and unlock data to make it unreadable or readable.

  3. Secrets are pieces of keys. That is, they work together in a variety of ways to secure your data. Secrets combine to create encryption keys, allow servers to double-check and verify that a key is up to date, and verify that requests for access to your data are from authorized key holders.

# A Strong Chain: Keys, Tenant Secrets, and Master Secrets

  1. Keys and secrets work together to provide layers of security. Think of what makes safety deposit boxes so secure. You have one of the keys that opens your deposit box, but first you have to get inside the bank vault. 

  2. Tenant secrets and master secrets are keys for keys, or that extra layer of protection like the bank teller and vault guard. If hackers get your key, they also must navigate the secret decryption process controlled by the master and tenant secrets before they can use your key.

  3. Salesforce generates a new master secret three times a year, with each release. Here’s how secret this secret is: It’s created by a dedicated processor called a hardware security module (HSM) specially designed for creating strong and secure cryptographic keys. '

# Enable Shield Platform Encryption

  1. Shield Platform Encryption is available for free in Developer Edition orgs. All other editions require you to purchase a license. 

  2. The data is encrypted with a stronger 256-bit AES key, and subscribers can manage access to their data with a wider range of keys and permissions. Shield Platform Encryption even allows you to search for encrypted data in databases.

  3. To enable platform encryption
    
    * Provision your license.

    * Assign permissions

    * Enable Shield Platform Encryption for your org.

# Assign Permissions and Create a Tenant Secret

  1. From Setup, enter Permission Sets

  2. Click New and enter label name 

  3. In the System section of the Key Manager page, select System Permissions.

  4. Click Edit, and enable the Customize Application and Manage Encryption Keys permissions.

  5. Click Save.

  6. From Setup, enter Users in the Quick Find box, then select Users.

  7. Select desired user, Scroll down to Permission Set Assignments, and select Edit Assignments.

  8. Selected created permission and save

# Generate a Tenant Secret

  1. From Setup, in the Quick Find box, enter Platform Encryption, and then select Key Management.

  2. Select Data in Salesforce from the Choose Tenant Secret Type list. Tenant secret types allow you to specify which kind of data you want to encrypt with a tenant secret. We’ll start by encrypting data in the core Salesforce database for now.
 
  3. Select Generate Tenant Secret.

# Update Tenant secret 

  1. From Setup, in the Quick Find box, enter Platform Encryption, and then select Key Management.

    * The Status column in the Key Management view identifies tenant secrets as either Active, Archived, or Destroyed.

  2. Select a tenant secret type from the list.

  3. To generate a new tenant secret, click Generate Tenant Secret. This action archives the previously active tenant secret of that type.

    * Archived tenant secrets can’t encrypt new data, but the app uses these archived keys to decrypt the data that was previously encrypted with it.

# Encrypt Fields, Files, and Attachments (standard ones)

  1. From Setup, in the Quick Find box, enter Platform Encryption, and then select Encryption Policy.

  2. Select Encrypt Fields.

  3. Click Edit.

  4. Select the fields you want to encrypt, and click Save.

# Encrypt Files and Attachments 

  1. From Setup, in the Quick Find box, enter Platform Encryption, and then select Encryption Policy.
  
  2. Select Encrypt Files and Attachments.

  3. Click Save.

# Encrypt Only Where Necessary

  1. Define a threat model for the organization. Walk through a formal threat-modeling exercise to identify which threats are most likely to affect the organization. Use these findings to create a data classification scheme and to decide which data to encrypt.

    * For example, certain kinds of threats might be specific to the financial sector or to the particular services that American Bank offers.

  2. Not all data is sensitive. Focus on information that requires encryption to meet regulatory, security, compliance, and privacy requirements.

  3. Understand that encryption applies to all users, regardless of permissions. The data stored in encrypted fields is encrypted at rest, regardless of user permissions. You reassure American Bank that even when their employees need to access encrypted data in the course of their work, their data is still encrypted at rest. They should use field-level access controls to limit who can access sensitive data.

  4. Combine encryption with other methods and levels of security such as ones provided by Salesforce

    * Some apps aren’t compatible with encryption and a few can prevent you from enabling Shield Platform Encryption.

  5. Set up a sandbox that mirrors the structure of their production org. From there, they can enable Shield Platform Encryption and experiment with how it does and doesn’t change the way their employees access information in their org.

    * When they turn on encryption in their sandbox org, Salesforce checks for potential side effects

