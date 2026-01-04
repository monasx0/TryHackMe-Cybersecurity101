# Active Directory Basiscs

## Task 1 - Introduction
Microsoft **Active Directory** manages devices and users within a corporate environment.It manages objects like users, computers, groups, printers, and shared folders.It helps us manage large, complex networks more easily and also enhanced security.In this room we will learn Active Directory Basics and will understand:
1. What Active Directory is
2. What an Active Directory Domain is
3. What are the main components of Active Directory
4. Forests and Domain Trust

To learn and understand this room, you should check the Windows Fundamentals room before starting this one.

## Task 2 - Windows Domains

### Domain
**Domain** is a logical group of multiple users and computers. It consists of objects such as, users, computers, and groups all of which are centrally managed. A domain helps us manage these objects from a single central point.

### Active Directory
**Active Directory** is a database and set of services that connect users with the network resources they need to get their work done. Active Directory contains critical information such as, what computers and users there are and who is allowed to do what. The server that runs Active Directory is known as **Domain Controller**.

The main advantage of having a configured windows domain are:
- **Centralized identity management**: All users across the network can be configured from Active Directory with minimum effort.
- **Managing security policies**: You can configure security policies directly from Active Directory and apply them to users and computers across the network as needed.

## Task 3 - Active Directory

### Active Directory Domain Services (AD DS)

The core of any Windows domain is **Active Directory Domain Services** (**AD DS**).
AD DS acts as a central directory that stores and manages information about all objects in the network, such as **users**, **computers**, and **groups**.

### Active Directory Objects

#### Users
Users are one of the most common objects in Active Directory. They are security principals, meaning they can be authenticated and assigned permissions to access network resources.
User can be represented as:
- **People**: Employees who need access to the network
- **Services**: Accounts used by services like IIS or MSSQL, which have limited privileges.
- #### Machines
- Each computer that joins a domain gets a **machine account** in Active Directory.
Machine accounts are also security principals and are mainly used by the system itself.
#### Security Groups
Security groups are used to assign permissions to multiple users or computers at once.
Instead of assigning permissions individually, users inherit access through group membership.

#### Organizational Units (OUs)
Organizational Units are containers used to organize users and computers and apply policies.
#### Active Directory Users and Computers
It is the main tool used to manage users, groups, computers and organizational units. Using **Active Directory Users and Computers**, administratos can create accounts, modify properties, and reset passwords.

## Task 4 - Managing Users in Active Directory
### Deleting extra OUs and users
Suppose we've been told to delete an extra **OU** department as it was closed due to budget cuts. If you try to delete it by right-click and delete the OU, you will get the error that you do not have sufficient privileges to delete this.

By default, OUs are protected against accidental deletion. To delete the OU, we need to uncheck a security feature. To do this, go to view, Advance Features, Object menu and you will see a check box called protect object from accidental deletion. Just uncheck it and you are done to delete the OU. 

#### Delegation
**Delegation** is the process of giving specific user some control over OUs. Delegation allows us to do advanced tasks on OUs without needing a Domain Administrator.

## Tak 5 - Managing Computers in Active Directory
By default, when a computer joins an Active Directory domain, it is placed in the **Computers container**.
If you open the Computers container, you will see:
- Servers
- Laptops
- Desktops

You will see all devices are mixed together by default. Keeping all devices in one container is not a good choice because laptop and desktop users need different settings, and servers need stricter security policies.

#### Better way to organize machines
Most organizations divide machines into at least these three categories:
- **Servers** – Machines running services (file servers, web servers, etc.)
- **Workstations** – Laptops and desktop PCs used by employees
- **Domain Controllers** – Manage the Active Directory Domain

By organizing computers into separate groups or OUs, administrators can apply appropriate policies to each type of device more effectively.

## Task 6 - Group Policies

#### Group Policy Objects

**GPOs** are simply a collection of settings that can be applied to OUs. It can contain settings which are either for users or computers.

To configure **GPOs**, you can use the Group Policy Management tool, available from the start menu.

#### GPO distribution
GPOs are distributed to the network via a network share called **SYSVOL**, which is stored in the DC. All users in a domain should typically have access to this share over the network to sync their **GPOs** periodically.

Once a change has been made to any **GPOs**, it might take up to 2 hours for computers to catch up.

## Task 7 - Authentication Methods

When a user tries to log in to any service using domain credentials, that service checks with the Domain Controller to confirm the login is correct. 
Windows domains use two main protocols for network authentication.

#### Kerberos Authentication
**Kerberos** is the default authentication in recent Windows versions. Users get tickets when they log in, which act as proof of authentication. They can show these tickets to access services without logging in again.

#### NetNTLM Authentication
In **NTLM authentication**, the client sends a login request to the server, which replies with a random challenge. The client combines this challenge with their password hash to create a response and sends it back. The server forwards this to the Domain Controller, which verifies it. If the response matches, the client is authenticated, and the result is sent back through the server.

## Task 8 - Trees, Forests and Trusts
#### Trees
In **Active Directory**, a **tree** is a hierarchy of domains that share a common namespace. It starts with a root domain and branches into child domains, helping organize users, computers, and resources logically.

#### Forests
A **forest** is a collection of one or more AD trees that share a common schema and global catalog. It’s the top-level container in Active Directory, allowing different trees to coexist while maintaining separate namespaces.

#### Trust Relationships
**Trust relationships** let users in one domain or forest access resources in another. They can be one-way or two-way and define which domains or forests trust each other.


## Task 9 - Conclusions
In this room we talked about the basic concepts of **Active Directory**. This room was only an introduction to the Active Directory, as there's a quite a bit more to explore in terms of domains, users and resource management.

#### What I Learned

1. **Active Directory Basics**: AD manages users, computers, groups, and resources centrally, making large networks easier and more secure.
2. **Domains and Objects**: A domain is a central group of users and computers, with objects like users, machines, and security groups organized in OUs
3. **Managing Users and Computers**: Administrators can create, delete, or delegate control of users, OUs, and computers, organizing devices into servers, workstations, and DCs.
4. **Group Policies and Authentication**: GPOs control settings for users and computers; Kerberos and NTLM are used to authenticate users in the domain.
5. **Trees, Forests and Trusts**: Trees are hierarchies of domains, forests are collections of trees, and trust relationships allow access between domains or forests.





