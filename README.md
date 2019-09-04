 [Demo](https://kunz398.github.io/Custom-FrontEnd-Validation/)
Validation:
i have used bootstrap to give the form an appealing look (dont really need bootstrap to make it work)
in order to use include this files in your html file
```
<link rel="stylesheet" href="validation.css">

<script src="https://code.jquery.com/jquery-3.4.1.js"></script>
<script src="validation.js"></script>
```
there are 5 parameters accepted by `validationForm` function:

 1. Parameter One
The id of the field you need to validate but if it is a radio element or a select element (drop-down) you need to pass its name in the first parameter  *(String)*

 2. Parameter Two
The id of the place you want your Validation message to show *(String)*

 3. Parameter Three
 The type of validation you need to do *(String)*

 4. Parameter Four *(optional)*
 The type of input field you need to validate *(String)*
 

 5. Parameter Five *(optional)*
 This parameter enables users to choose weather they want the success messages to show under the radio element or select element *(Boolean)*  
 
 ## More on parameter two:: Types of Validation
 
```
    <input type="text" id="exampleID" name="exampleName" />
    <span id="exampleMessage"></span>
    
    //single upload
    <input class="upload-file" type="file" name="exampleUploadName" id="exampleUploadId"/>
    <span id="exampleUploadMessage"></span>
      //multiupload
    <input class="upload-file" type="file" name="exampleMultiUploadName" id="exampleMultiUploadId" multiple/>
    <span id="exampleMultiUploadMessage"></span>
    //radio
    <input autocomplete="off" type="radio" class="custom-control-input" id="num_1" value="num_1"   name="radioboxes">
 <input autocomplete="off" type="radio" class="custom-control-input" id="num_2" value="num_2"   name="radioboxes">
 <span id="radioboxesMsg"></span>
 //checkbox
 <input type="checkbox" name="myCheckBoxes" value="checkbox One" >
 <input type="checkbox" name="myCheckBoxes" value="checkbox Two">
 <span id="myCheckBoxesMsg"></span>
 //select (drop down)
 <select id="select" name="mySelect">  
 <option selected value="">Open this select menu</option>  
 <option value="1">One</option>  
 <option value="2">Two</option>  
 <option value="3">Three</option>  
</select>  
<div id="selectMsg"></div>
```

|Description|Snippet | Explanation |
|--|--|--|
|  field is required| `validationForm("exampleID","exampleMessage","required|")` | Write the id as first parameter and the place where message will be displayed as the second parameter then writed required followed by a pipe symbol. this will mean that the field is required.
 |minimum characters and field is required |`validationForm('exampleID', 'exampleMessage', "required|min:2")`|This means that the form will only be submitted if the characters in the field is more then 2 characters |
 |Only Alphabets|`validationForm('exampleID', 'exampleMessage', "alpha|")`|This means that the form will only be submitted if the charactersare alphabets|
|Only numbers|`validationForm('exampleID', 'exampleMessage', "numeric|")`|This means that the form will only be submitted if the characters in the field are numbers|
|email|`validationForm('exampleID', 'exampleMessage', "email|")`|This means that the form will only be submitted if its a valid email address|
|single file upload|`validationForm('exampleUploadId', 'exampleUploadMessage', "required|file:[png,jpg,jpeg]|fileSize:5]")`|for a single file upload you need to specify that is a file followed by a colon and pass an array of valid file extension also you may pass in the size in mbs `fileSize:MB`|
|Multi file upload|`validationForm('exampleMultiUploadId', 'exampleMultiUploadMessage', "required|multifile:[png,jpg,jpeg]|multiFileSize:2]")`|for a multifile upload you need to specify that is a multi file followed by a colon and pass an array of valid file extension also you may pass in the size in mbs `fileSize:MB`|
|radio buttons|`validationForm('radioboxes', 'radioboxesMsg', "required|", 'radio',true)`|the first parameter requires the name of the radio box, the second parameter requires where the message would be shown, the third parameter requires the type of validation which will be usually `required|` the 4th parameter is required for radio box which will specify that this is a radio button and the fifth parameter is optional (by default its true) this will show the message on success and what u have selected under the input |
|Check Box|`validationForm('myCheckBoxes', 'myCheckBoxesMsg', "required|",'checkbox',false)`|the first parameter requires the name of the checkbox, the second parameter requires where the message would be shown, the third parameter requires the type of validation which will be usually `required|` the 4th parameter is required for checkbox which will specify that this is a check box and the fifth parameter is optional (by default its true) this will show the message on success and what u have selected under the input |
|Select (drop down)|`validationForm('select', 'selectMsg', "required|",'select',false)`|the first parameter requires the ID of the select , the second parameter requires where the message would be shown, the third parameter requires the type of validation which will be usually `required|` most of the time, the 4th parameter is required for select which will specify that this is a select and the fifth parameter is optional (by default its true) this will show the message on success and what u have selected under the input |

## How to check if all validation has passed 
since the `validationForm()` function returns a Boolean you can store it in a array like so:
```
...
let isvalid = []; // make an array
isvalid.push(validationForm("exampleID","exampleMessage","required|"));
isvalid.push(validationForm('exampleID', 'exampleMessage', "alpha|"));
isvalid.push(validationForm('select', 'selectMsg', "required|",'select',false));
isvalid.push(validationForm('exampleMultiUploadId', 'exampleMultiUploadMessage', "required|multifile:[png,jpg,jpeg]|multiFileSize:2]"))

//and then you can check if the array contains any 'false'

if (jQuery.inArray("false", isvalid) != -1) {  
  // if false is found in the array  
  
} else {
//if all validation passes you can perform your form submission or Ajax call:
}
```
you can see the demo here [Demo](https://kunz398.github.io/Custom-FrontEnd-Validation/)
 
