# artifact-creator
This app can use to create update artifacts and generate the script to run in the console.

### How to use
copy the jar files from jenkins and last wum updated product to the same location as the gen.js script file and unzip them.

If you list the folders, it should look like bellow.

```
gen.js                                                
org.wso2.carbon.apimgt.publisher.feature-6.6.163/     
org.wso2.carbon.apimgt.store.feature-6.6.163/         
wso2am-3.1.0/
```

Update the params in the gen.js according to the patch info similar to bellow.

( You can uncomment/uncomment web apps according to the list of web apps you'r patching )

For an example following config is only checking the publisher and devportal webapps.

```js
// ******************************************************** //
// ******************************************************** //
// ******************************************************** //
//          This part need to modified accordingly          //
    const jars = [
    {
        jarName: 'org.wso2.carbon.apimgt.publisher.feature-6.6.163',
        appContext: 'publisher',
    },
    {
        jarName: 'org.wso2.carbon.apimgt.store.feature-6.6.163',
        appContext: 'devportal',
    },
    // {
    //     jarName: 'org.wso2.carbon.apimgt.admin.feature-6.6.163',
    //     appContext: 'admin',
    // }
]


const productName = 'wso2am-3.1.0';
const artifactFolderName = '0390';


// ******************************************************** //
// ******************************************************** //
// ******************************************************** //
```
You need to have node 10+ version installed.

```bash
node gen.js
```

running above command will create the artifact folder and copy the files accordingly to it.

It will also gen a script file to run in the browser console to add the files during PR analysis.

