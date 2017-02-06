# ProgrammingAssignment2
#  This function creates a special "matrix" object that can cache its inverse
makeCacheMatrix <- function(x = matrix()) {
            inv <- NULL
            set <- function(y) {
                      x <<- y
                      inv <<- NULL
                  }
            get <- function() x
            setinverse <- function(inverse) inv <<- inverse
            getinverse <- function() inv
            list(set = set, get = get,
                                            setinverse = setinverse,
                                            getinverse = getinverse)
}


# This function computes the inverse of the special "matrix" returned by makeCacheMatrix 
# above. If the inverse has already been calculated (and the matrix has not changed), 
# then the cachesolve should retrieve the inverse from the cache.
# Computing the inverse of a square matrix can be done with the solve function in R. 
# For example, if X is a square invertible matrix, then solve(X) returns its inverse.

#For this assignment, assume that the matrix supplied is always invertible

cacheSolve <- function(x, ...) {
                 inv <- x$getinverse()
                 if(!is.null(inv)) {
                               message("getting cached data")
                               return(inv)
                           }
                 data <- x$get()
                 inv <- solve(data, ...)
                 x$setinverse(inv)
                 inv
             }
