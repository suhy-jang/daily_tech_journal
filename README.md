# daily_tech_journal

# Data structures

```
Data structures (non-primitive)
│
├─ Linear data structures
│  ├─ Array
│  ├─ Linked list
│  ├─ Stack
│  └─ Queue
│
└─ Non linear data structures
   │
   ├─ Graphs
   ├─ Trees
   ├─ Trie
   └─ HashTable
      │
      ├─ Set
      └─ Map
```

#### The differences between Stack and Queue (16.jan.2020)

Queue uses First Input First Output (FIFO). For instance, the people wait for a queue to hop on the bus, the first person in the line will get on the bus.

Stack uses Last Input First Output (LIFO). For example, when I put one piece of paper on the stack of papers, some others will pick first that paper what I put from the pile.

#### The differences between Array and Linked list (14.jan.2020)

The Array is a consistent set of a fixed number of data items. And the Linked list is an ordered set comprising a variable number of data items.

The indexes directly or randomly access the Array. But the Linked list is sequentially accessed, traverse starting from the first node in the list by the pointer.

The Array relatively slow at insertion or deletion as shifting is required, but the Linked list is effective, fast and efficient for that.

However, access time in memory of Linked list is slower. Because, While Array elements physically assigned consecutively in the hardware memory during compile time, Linked list elements are stored randomly in hardware during the run time.

The linear search can search them both. But Array can be searched by binary search, while Linked list is not.

# Computer Networking

## Network Layers

Two computers communicate help of network connection. But, if this two has different OS or architecture or even different capacity of data acceptance speed,
how they can communicate with each other in real-time.

#### Five-layer internet protocol stack (15.jan.2020)

```
Protocol stack
│
├─ Application
├─ Transport
├─ Network
├─ Link
└─ Physical
```

Each layers is a package of protocols.

The Application layer includes some protocols, such as the HTTP, SMTP, FTP protocol. It also does transmitting human-readable url domain to the actual address.
Application layer data transported by TCP, UDP protocols in the Transport layer.

Network layer moves Datagram packets from one host to another.
The Network layer combines Transport layer segment and a destination address, like a postal service a letter with a destination address.

The Network layer passes the Datagram down to the Link layer, and the Link layer passes the Datagram up to the Network layer.

Finally, the job of the Physical layer is to move the individual bits within the frame from one node to the next.

But we should mention that it has not only protocol stack around. The network can be organized around seven layers which is OSI (Open System Interconnection) model.

#### 7 layers of OSI model (15.jan.2020)

```
OSI model
│
├─ Application
├─ Presentation
├─ Session
├─ Transport
├─ Network
├─ Data link
└─ Physical
```

OSI(Open System Interconnection) model has 7 layers.

Application layer includes HTTP, FTP, SMTP, ... protocols. That provides services of network applications such as Chrome, Firefox, Outlook, Skype, etc.

Presentation layer receives data from the Application layer. This data is the form of characters and numbers and translated to
machine understandable binary format. And Presentation layer compresses this data for faster sending, also does encryption or decryption.

Session layer helps session management, authentication, authorization.

The Transport layer is envolved segmentation, flow control for speed differences, error control, connection-oriented and connection-less transmission.

The Transport layer provides various forms of process-to-process communication by relying on the network layer's host-to-host communication service.

The function of the Network layer is logical addressing of IPv4 and IPv6, path determination and Routing. When the data arrives, the Routing does finding where to move data with the separation of host and computer address.

Their has two types of addressing, logical addressing is from the Network layer, and physical addressing is from Data link layer.
The Data link layer is embedded as software in the network interface card of the computer.

Physical layer considered by the data communication through optic, electrical transmitting information.

### TCP

#### Three-Way Handshake (14.jan.2020)

We supposed to try a network connection such as opening google.com, what is going to have happened?

1. A client sends to server SYN packet which contains sequence numbers that support the server can connect client; this step is like "Hey, do you want to talk?"
2. The server sends back to the client SYN/ACK packet with the help of sequence numbers; this step is like "Yeah, I received your message, do you want to talk?"
3. Then the client sends ACK packet to the server, like "Yes, let's talk."

=> After this three-way Handshake occurs, the connection is established between the server and the client. Now the packets between them can be transmitted. The protocols loading over TCP is HTTP, FTP, SMTP and SSH.

As it has an opening connection, it also has a closing connection.

1. The client sends the server SYN/ACK packet; "There is no need connection, wants to leave."
2. The server sends back to the client ACK packet, "Yes, I know that you want to leave, then bye."
3. The client sends back to the server ACK packet, "Yes, bye!"

# An introduction about Rails 6 framework

This writing is to introduce Rails framework which is a server-side web app framework to a person new to and inexperienced in Rails.

```
source /
│
├─ app /
│  ├─ controllers
│  ├─ models
│  └─ views
│
├─ config /
│  └─ routes
│
└─ db /
   └─ migrate
```

#### MVC (13.jan.2020)

Rails has a model-view-controller (MVC) design pattern. It presents default structures for a database, a web service, and web pages. I am going to talk about this today.

The model contains data for application and often linked to a database. And it has an order which can be used for business purpose. And it does not know user interface; it means it can be reused.

The view generates the user interface, which presents data to the users. Many views can access the same model for different reasons. Once the view created, the data is displayed to the users.

The controller receives events from the outside world, usually through views. It interacts with the model and displays the appropriate view to the users.

#### Routes (14.jan.2020)

```
source /
│
├─ app /
│  └─ controllers /
│     └─ users_controller.rb
│
└─ config /
   └─ routes.rb

[ users_controller.rb ]
  def index
    @users = User.all
  end

[ routes.rb ]
  get 'users#index', as: :users
```

The Router in rails navigates the URL or path to proper controllers. For example, the Router 'users URL' called by external links such as user input or command line, then it will connect to 'users_controller' 'index' method.
