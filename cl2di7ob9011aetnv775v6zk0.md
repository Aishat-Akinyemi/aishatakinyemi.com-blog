## How to create Near AssemblyScript smart contract project.

In this article, I’ll walk you through how to setup NEAR smart contracts in AssemblyScript project in few mins. You will find a copy of the project built following these instructions in this [github repository](https://github.com/Aishat-Akinyemi/Near-AssemblyScript-Contract-template),  be sure to follow the steps through to see how it all came together.

## Assumption

I assume you have set up your local NEAR smart contract development environment, you can [check out this guide](https://aishatakinyemi.com/set-up-your-local-development-environment-for-near-smart-contracts) if you haven’t done so.

## Steps to create your Near Assemblyscript smart contract project

1. Create a folder for the project, give it a suitable name
2. Run `npx asinit .` 
3. In the terminal, add near-sdk-as by running `yarn add -D near-sdk-as` 
4. Rename the `build` folder to `out` . We’re trying to follow the official near practice as much as possible. When we build the project, the output WASM file should be put in this folder.
5. Remove the contents of the `asconfig.json` file in the root. The file should contain the following config code.
    
    ```json
    {
      "extends": "near-sdk-as/asconfig.json",
      "outDir": "./out"  
    }
    ```
    
    The second line of the above code means that when we build the project, the output WASM file should be put in a folder named `out` .
    
6. Add a new file named `as-pect.config.js` file in the root folder. The file should contain the following config code
    
    ```jsx
    module.exports = require("near-sdk-as/imports");
    ```
    
7. Delete the `index.js` file from the root folder.
8. Delete the `tests` folder. Our tests will be saved in another location.
9. Run the following set of commands:
    
    ```jsx
    cd assembly && touch as_types.d.ts && mkdir __tests__  && cd __tests__ && touch as-pect.d.ts main.unit.spec.ts
    ```
    
    The `assembly` folder would contain our smart contract code, tests and some configuration files. 
    The command did the following:
    
    - it added the assembly-script type definition file `as_types.d.ts` wherein we would add references to include near-sdk-as types
    - it created a `__tests__` folder for our As-spect tests and adds test file  `main.unit.spec.ts` and type definition file `as-pect.d.ts`.
10. In `assembly/as_types.d.ts` add this
    
    ```
    /// <reference types="near-sdk-as/assembly/as_types" />
    
    ```
    
11. In `assembly/__tests__/as-pect.d.ts` add this
    
    ```tsx
    /// <reference types="@as-pect/assembly/types/as-pect" />
    ```
    
12. Edit the `scripts` in the `package.json` 
    
    Remove the `scripts`  values and have the below code instead.  Leave everything else as is.
    
    ```json
    {
    		"scripts": {
        "build": "yarn asb",
        "initialise:test": "yarn asp --init",
        "test": "asp --verbose -f unit.spec"
      },
    		...
    }
    ```
    
13. In the terminal, go back to the project root folder to initialise git by running in root folder `git init & touch .gitignore` 
14. In the `gitignore` file add `node_modules`
15. After all the above step your file structure should be similar to this
    
    ```json
    assembly                        
    │    ├──__tests__                                               
    │    │   ├── as-pect.d.ts          
    │    │   └── main.unit.spec.ts  
    │    ├──as_types.d.ts           
    │    ├──index.ts                
    │    └──tsconfig.json            
    ├── node_modules  
    ├── out         
    ├── .gitignore                 
    ├── as-pect.config.js            
    ├── asconfig.json               
    ├── package.json                 
    └── yarn.lock                   
    ```
    

### Let’s add some sample code to test our setup (optional step).

1. Create a simple call function `getString` on the smart contract, it returns the passed in string. Paste the code below into `assembly/index.ts`
    
    ```tsx
    import { logging, Context } from "near-sdk-as";
    
    export function getString(str: string):string{
      logging.log(`${Context.sender} said ${str}`);
      return str;
    }
    ```
    
2. Add unit tests for the above function into  `assembly/__tests__/main.unit.spec.ts`
    
    ```tsx
    import { Context, VMContext } from 'near-sdk-as';
    import { getString } from '../index';
    
    const setCurrentAccount = (): void => {
      VMContext.setCurrent_account_id('alice');
    };
    
      describe('', () => { 
      beforeEach(() => {
        setCurrentAccount;    
      });
        
      it('returns the input string', () => { 
        expect(getString("hello world")).toBe("hello world", "should have returned the input string");
      });      
    });
    ```
    
3. Let’s test our smartcontract by running `npm run test`.
4. Build the project by running `npm run build`. This would result in a .wasm file being added in `out/release` folder.
5. To deploy into the d the newly compiled wasm file
    
    ```bash
    near dev-deploy <path to output wasmFile>
    ```
    
     e.g. in my case I ran `near dev-deploy out/release/Near-AssemblyScript-Contract-template.wasm`
    
    You can now call our smart contract function  with near cli, you can read more on  how to use near-cli here.
    
    You are all set!, you may now start building those awesome contracts — happy building 💫.
    
    ### Resources
    
    Learn and Earn Near by enrolling in [NEAR 101 course](https://dacade.org/communities/near/courses/near-101) on Dacade.