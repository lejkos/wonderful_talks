Haskell Useful Stuff
====================

HTTP
----
::

  https://github.com/snoyberg/http-client/blob/master/TUTORIAL.md

    #!/usr/bin/env stack
    -- stack script --resolver lts-12.21
    {-# LANGUAGE OverloadedStrings #-}
    import qualified Data.ByteString.Lazy.Char8 as L8
    import           Network.HTTP.Simple

    main :: IO ()
    main = do
        response <- httpLBS "http://httpbin.org/get"

        putStrLn $ "The status code was: " ++
                   show (getResponseStatusCode response)
        print $ getResponseHeader "Content-Type" response
        L8.putStrLn $ getResponseBody response
