CIModuleAanTelevisionToevoegen.png
````mermaid

sequenceDiagram
participant Client as Actor
participant TelevisionController
participant TelevisionService
participant TelevisionRepository
participant CIModuleRepository

     Client->>+TelevisionController: 1: assignCIModuleToTelevision(TelevisionID , CIModuleID)
     TelevisionController->>+TelevisionService: 2: assignCIModuleToTelevision(TelevisionID , CIModuleID)
     TelevisionService->>+TelevisionRepository: 3: findById(TelevisionID)
     TelevisionRepository->>-TelevisionService: 4: Optional<Television>
     TelevisionService->>+CIModuleRepository: 5: findById(CIModuleID)
     CIModuleRepository->>-TelevisionService: 6: Optional<CIModule>
     TelevisionService->>TelevisionService: 7: setCIModule(CIModule)
     TelevisionService->>+TelevisionRepository: 8: save(television)
     TelevisionRepository->>-TelevisionService: 9: Television
     TelevisionService->>-TelevisionController: 10: void
     TelevisionController->>-Client: 11: Http Status 200 OK

````
RemoteControllerAanTelevisionToevoegen.png
````mermaid

sequenceDiagram
participant Client as Actor
participant TelevisionController
participant TelevisionService
participant TelevisionRepository
participant RemoteControllerRepository


    Client->>+TelevisionController: 1: assignRemoteControllerToTelevision(TelevisionID , RemoteControllerID)
    TelevisionController->>+TelevisionService: 2: assignRemoteControllerToTelevision(TelevisionID , RemoteControllerID)
    TelevisionService->>+TelevisionRepository: 3: findById(TelevisionID)
    TelevisionRepository->>-TelevisionService: 4: Optional<Television>
    TelevisionService->>+RemoteControllerRepository: 5: findById(RemoteControllerID)
    RemoteControllerRepository->>-TelevisionService: 6: Optional<RemoteController>
    TelevisionService->>TelevisionService: 7: setRemoteController(remoteController)
    TelevisionService->>+TelevisionRepository: 8: save(television)
    TelevisionRepository->>-TelevisionService: 9: Television
    TelevisionService->>-TelevisionController: 10: void
    TelevisionController->>-Client: 11: Http Status 200 OK
````

WallBracketAanTelevisionToevoegen.png
````mermaid

sequenceDiagram
participant Client as Actor
participant TelevisionWallBracketController
participant TelevisionWallBracketService
participant TelevisionRepository
participant WallBracketRepository
participant TelevisionWallBracketRepository


    Client->>+TelevisionWallBracketController: 1: addTelevisionWallBracket(TelevisionId , WallBracketId)
    TelevisionWallBracketController->>+TelevisionWallBracketService: 2: addTelevisionWallBracket(TelevisionId , WallBracketId)
    TelevisionWallBracketService->>+TelevisionRepository: 3: findById(televisionId)
    TelevisionRepository->>-TelevisionWallBracketService: 6: Optional<Television>
    TelevisionWallBracketService->>+WallBracketRepository: 7: findById(wallBracketId)
    WallBracketRepository->>-TelevisionWallBracketService: 10: Optional<WallBracket>
    TelevisionWallBracketService->>TelevisionWallBracketService: 11: setTelevision(television)
    TelevisionWallBracketService->>TelevisionWallBracketService: 12: setWallBracket(wallBracket)
    TelevisionWallBracketService->>+TelevisionWallBracketRepository: 13: setId(id)
    TelevisionWallBracketRepository->>-TelevisionWallBracketService: 16: TelevisionWallBracket
    TelevisionWallBracketService->>-TelevisionWallBracketController: 17: Optional<TelevisionWallBracket>
    TelevisionWallBracketController->>-Client:  19: Http status 201 CREATED
````
