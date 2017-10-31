/* CALLING FUNCTIONS */
var updateZip = function() {
  console.log(this);
}

var newObj = {
  val: "133231",
  newFunc: function thisFunct() {
    console.log(this);
  }
}

updateZip();
updateZip.call({});
updateZip.call({
  zip: '80631'
});
newObj.newFunc.call(newObj);

/* APPLYING */
var foo = function(arg1, arg2){
  console.log(arg1 + " " + arg2);
}
foo.apply({},[12,15]);
