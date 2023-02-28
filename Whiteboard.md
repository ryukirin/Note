# Whiteboard

## System Structure

![image-20230224130611829](https://raw.githubusercontent.com/ryukirin/Note/main/image/image-20230224-2.png)

- user voice send to the whiteboard with speech recognition function, after being recognized as text, it is sent to the server.
- After storing node and relationship into RDF database, send the node and relationship information to whiteboard.

## Use Case

- When entering the next phase, clear other nodes, or move other nodes to places where the window cannot see, and only the nodes in the previous stage will be displayed. 

  And if the nodes have classification,  whiteboard can put nodes of the same classification together and display the classification name.

  ![image-20230224131258343](https://raw.githubusercontent.com/ryukirin/Note/main/image/image-20230224-1.png "example of entering the next phase")

- During the current phase, the nodes of the previous phase are always displayed.

  And the node and relationship of current phase will be displayed on whiteboard.

  ![image-20230224133006710](https://raw.githubusercontent.com/ryukirin/Note/main/image/image-20230224-3.png "example of during the current phase")

## Functional Requirement

- Display node and relationship 

  - One or more node information (example: node_id and node_content) and one or more relationship information (example: start_node_id, end_node_id, relationship) can be received and displayed them on whiteboard.

  - If the 'node_id' already exists, change the node content.

  - If the node has classification, whiteboard can put nodes of the same classification together and display the classification name.

  - Example of data sent to whiteboard (one node and one relationship, node "problem001" already exists)

    ```json
    {
      	"node": [{
          	"node_id": "cause001",
          	"node_content": "cause content 001",
          	"class_id": "class001",
          	"class_name": "cause class001 content",
      	}],
      	"lines": [{
          	"start_node_id": "problem001",
          	"end_node_id": "cause001",
          	"relationship": "cause"
      	}]
    }
    ```

- Can delete all displayed nodes or some of them.

- Speech recognition

  - The user's speech can be recognized as text(with or without punctuation) and can be returned together with user id.

  - I hope that one speech content returned by the whiteboard can be used as a complete speech of a user.

  - Example of data sent to server

    ```json
    {
        "user_id": "user001",
        "user_speech": "user speech content"
    }
    ```
