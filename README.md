# TicTacToe
TicTacToe game using REST APi and JSON Resp
Tic-Tac-Toe RESTful Service

This is a RESTful service for play tic-tac-toe ganme. It implements by Java with Jersey framwork and Grizzy web framwork.
Getting Start

The url will be

  http://localhost:8080/tictactoe/api/v1.0/game

* GET, POST, PUT and DELETE

This RESTful service is statful. Which mean each new session will store every game status. You can use curl command or postman app to use this service. Strong suggest to using postman. It will be easy to handle cookies. All response data is in json format. There are two different types:

    Game data example:

{"id":"66177c60-e209-4461-8a94-c5cd9bea295c","dimension":3,"grid":[[0,0,0],[0,0,0],[0,0,0]],"status":"START","winner":0,"lastUpdateTime":1505793050913}

    Error massage example:

{"message":"Game not found for ID: 6344700d-62e3-4870-9676-7149ef5e925f"}

    Start new session

    If you just start the service, there is no session data in the system. You can use GET ALL api to start a new session. HTTP GET Request URL: http://localhost:8080/tictactoe/api/v1.0/game/all

    curl command:

    curl --cookie-jar headers.txt -H "Content-Type: application/json" http://localhost:8080/tictactoe/api/v1.0/game/all

    !!!! Only use --cookie-jar at first time !!!!

    Get all games

    http://localhost:8080/tictactoe/api/v1.0/game/all
    Method 	URL Parameter 	Request Payload 	Response Body
    GET 	game id 	Empty 	games map json object

    Response Example:

    {"66177c60-e209-4461-8a94-c5cd9bea295c": {"id":"66177c60-e209-4461-8a94-c5cd9bea295c","dimension":3,"grid":[[0,0,0],[0,0,0],[0,0,0]],"status":"START","winner":0,"lastUpdateTime":1505793050913}}

    curl command:

    curl -b headers.txt -H "Content-Type: application/json" http://localhost:8080/tictactoe/api/v1.0/game/all

    Create a new game

    http://localhost:8080/tictactoe/api/v1.0/game
    Method 	URL Parameter 	Request Payload 	Response Body
    POST 	None 	Empty 	game json object

    Response Example:

    {"id":"66177c60-e209-4461-8a94-c5cd9bea295c","dimension":3,"grid":[[0,0,0],[0,0,0],[0,0,0]],"status":"START","winner":0,"lastUpdateTime":1505793050913}|

    curl command:

    curl -b headers.txt -H "Content-Type: application/json" -X POST http://localhost:8080/tictactoe/api/v1.0/game

    Get game

    http://localhost:8080/tictactoe/api/v1.0/game/66177c60-e209-4461-8a94-c5cd9bea295c
    Method 	URL Parameter 	Request Payload 	Response Body
    GET 	game id 	Empty 	game json object

    Response Example:

    {"id":"66177c60-e209-4461-8a94-c5cd9bea295c","dimension":3,"grid":[[0,0,0],[0,0,0],[0,0,0]],"status":"START","winner":0,"lastUpdateTime":1505793050913}

    curl command:

    curl -b headers.txt -H "Content-Type: application/json" http://localhost:8080/tictactoe/api/v1.0/game/66177c60-e209-4461-8a94-c5cd9bea295c

    Update game

    http://localhost:8080/tictactoe/api/v1.0/game/66177c60-e209-4461-8a94-c5cd9bea295c
    Method 	URL Parameter 	Request Payload 	Response Body
    PUT 	game id 	game json object 	game json object

    Request Payload Example:

    {"id":"66177c60-e209-4461-8a94-c5cd9bea295c","dimension":3,"grid":[[1,0,0],[0,0,0],[0,0,0]],"status":"START","winner":0}

    Response Example:

    {"id":"66177c60-e209-4461-8a94-c5cd9bea295c","dimension":3,"grid":[[1,0,0],[0,0,0],[0,0,0]],"status":"PLAYING","winner":0","lastUpdateTime":1505793051888}

    curl command:

    curl -b headers.txt -H "Content-Type: application/json" -X PUT -d '{"id":"f7f2eda8-d548-4940-a45b-9728da36cccd","dimension":3,"grid":[[2,1,1],[0,0,0],[0,0,0]]}' http://localhost:8080/tictactoe/api/v1.0/game/f7f2eda8-d548-4940-a45b-9728da36cccd

    Update game and game end

    There are two situations the game will end. The game status value will be END.

        The game board full

        If no winner, then the winner value is 0.

        Has winner

        The winner value will be 1 (player 1) or 2 (player 2).

    Delete game

    http://localhost:8080/tictactoe/api/v1.0/game/66177c60-e209-4461-8a94-c5cd9bea295c
    Method 	URL Parameter 	Request Payload 	Response Body
    DELETE 	game id 	Empty 	Empty

    curl command:

    curl -b headers.txt -H "Content-Type: application/json" -X DELETE http://localhost:8080/tictactoe/api/v1.0/game/66177c60-e209-4461-8a94-c5cd9bea295c

* Build and run locally

