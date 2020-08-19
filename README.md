# React Mini Challenge: setState with Arrays

## Instructions

Fork this repo, then run `git clone` to download it locally. Then `cd` into the downloaded directory and open it in your text editor with `code .`.

To get started, run:

```
npm install
npm start
```

## Submitting

When you’re finished, run the following commands in your terminal to submit:

```
git add .
git commit -m 'Done'
git push
```

To get feedback on your code, make a [pull request from your forked repo](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork).

## Assignment

We're working a very simple todo app to give you some practice working with arrays in state. Most of the code is set up for you, so that all that's left for you is to use `setState` inside the `createTodo`, `deleteTodo`, and `updateTodo` methods. 

Make sure you aren't mutating the original array when you're setting state! Also make sure you aren't mutating any objects within the array.

## Tips
If you're stuck, have a look at these methods for working with arrays:

- [Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
- [.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [.filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

If you want more help, check out these common strategies for updating arrays in state *without* mutating the original array.

### Adding to an array
- Use the spread operator!

```js
addComment = newComment => {
  // spread to create a new array and add new comment at the end
  const updatedComments = [...this.state.comments, newComment] 

  this.setState({ 
    comments: updatedComments
  })
}
```

### Removing from an array
- Use filter!

```js
removeComment = commentId => {
  // filter to return a new array with the comment we don't want removed
  const updatedComments = this.state.comments.filter(comment => comment.id !== commentId) 

  this.setState({ 
    comments: updatedComments
  })
}
```

### Updating an item in an array
- Use map!

```js
updateComment = updatedComment => {
  // filter to return a new array with the comment we don't want removed
  const updatedComments = this.state.comments.map(comment => {
    if (comment.id === updatedComment.id) {
      // if the comment in state is the one we want to update, replace it with the new updated object
      return updatedComment
    } else {
      // otherwise return the original object
      return comment
    }
  }) 

  this.setState({ 
    comments: updatedComments
  })
}
```

If you only want to update one attribute instead of replacing the whole object:
```js

  // updating one object in an array
  handleUpdateCustomer = (id, name) => {
    // use map to return a new array so we aren't mutating state
    const updatedCustomers = this.state.customers.map(customer => {
      // in the array, look for the object we want to update
      if (customer.id === id){ // if we find the object
        const updatedCustomer = { ...customer } // make a copy of it
        updateCustomer.name = name // update whatever attribute have changed
        return updatedCustomer // return the updated copy
      } else { // for all other objects in the array
        return customer // return the original object
      }
    })

    // set state with our updated array
    this.setState({ customers: updatedCustomers })
  }  
```
