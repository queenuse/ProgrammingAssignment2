

makeCacheMatrix <- function(x = matrix()) {
    # Initialize an object to store the inverse
    inverse <- NULL
    
    # Function to set the matrix value and reset the inverse
    set <- function(matrix) {
        x <<- matrix
        inverse <<- NULL
    }
    
    # Function to get the matrix value
    get <- function() {
        x
    }
    
    # Function to get the cached inverse
    getInverse <- function() {
        inverse
    }
    
    # Function to cache the inverse
    cacheInverse <- function() {
        inverse <<- solve(x)
    }
    
    # Return a list of functions
    list(set = set,
         get = get,
         getInverse = getInverse,
         cacheInverse = cacheInverse)
}


    # Retrieve the cached inverse if it exists
    inverse <- x$getInverse()
    
    # If the inverse is not cached, calculate it and cache it
    if (is.null(inverse)) {
        message("Calculating inverse and caching")
        x$cacheInverse()
        inverse <- x$getInverse()
    } else {
        message("Retrieving cached inverse")
    }
    
    # Return the inverse
    inverse
}

  
