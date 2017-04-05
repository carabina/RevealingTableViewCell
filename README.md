# RevealingTableViewCell (experimental)
RevealingTableViewCell is a UITableViewCell that can be swiped to reveal content udnerneath it's main view.

---------
*__NOTE: At this early stage, this is an experimental project. Things might change quickly, with no backwards compatibility. Using this in production environments is not a good idea__*
---------



## Installation
Requires: `Swift 3`, `iOS 10`

### CocoaPods

```
pod 'RevealingTableViewCell'
```


## Usage
No code changes required, everything is done in Interface Builder.

Step 1  
Use RevealingTableViewCell (or your subclass of it) as a custom class for your tableview cell in Interface Builder.

Step 2  
Inside the cell's default `contentView`, put a subview and connect it to the the IBOutlet `uiView_mainContent`. This will be the view that slides sideways to reveal some content underneath. Using AutoLayout, pin this `uiView_mainContent` to it's superview using a constraint: `uiView_mainContent.centerX = superview.centerX`. Connect that constraint to `layoutConstraint`. (Do not pin the left/right sides of the `uiView_mainContent` to the `contentView`, but rather add a `equal width` constraint.)

Step 3  
Inside the cell's default `contentView`, put and connect `uiView_revealedContent_left` and/or `uiView_revealedContent_right` subviews. Pin them using AutoLayout to the corresponding sides of your cell. Fix their widths. Make sure they are behind the `uiView_mainContent`.

## Example project
`// TODO:`  

## Known issues and considerations
* At the moment it is required that all the 'hidden' views (the ones that are behind the main view and are revealed when sliding), are in the view hierarchy of the cell at all times, even if they are never to be shown. This might be a performance issue in some cases.
* The cell needs to have handlers for when the animations finish and report the state at which it ended.
