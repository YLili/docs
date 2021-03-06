# Contract.Migrate Method (byte[], byte[], byte, bool, string, string, string, string, string)

Migrate/renew smart contract. This method is similar to `Contract.Create`, the only difference being this method adds logic for migration of the private persistent store. When executing this method, it will migrate all **existing data** in the persistent store to the new contract.

If the contract does not utilise the persistent store, `Contract.Migrate` is functionally the same as `Contract.Create`.

Namespace: [Neo.SmartContract.Framework.Services.Neo](../../neo.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```c#
public static extern Neo.SmartContract.Framework.Services.Neo.Contract Migrate(byte[] script, byte[] parameter_list, byte return_type, bool need_storage, string name, string version, string author, string email, string description)
```

Parameters: 

script: The contract bytecode as a byte array.

parameter_list: Parameter list as a byte array. Refer to [Smart Contract Parameters and Return Values](../../../../tutorial/Parameter.md).

return_type: Return type as a byte. Refer to [Smart Contract Parameters and Return Values](../../../../tutorial/Parameter.md).

need_storage: If the contract requires a persistent store, boolean.

name: The name of the contract as a string.

version: The version as a string.

author: The author name as a string.

email: The author email as a string.

description: The description of the contract as a string.

Return value: [Contract](../Contract.md).

## Example

```c#
public class Contract1 : FunctionCode
{
    public static void Main(byte[] signature)
    {
        if(VerifySignature(new byte[] { 2, 133, 234, 182, 95, 74, 1, 38, 228, 184, 91, 78, 93, 139, 126, 48, 58, 255, 126, 251, 54, 13, 89, 95, 46, 49, 137, 187, 144, 72, 122, 213, 170 }, signature))
          {
                    //This is the scripthash of the new contract
        byte[] script = new byte[] { 116, 107, 0, 97, 116, 0, 147, 108, 118, 107, 148, 121, 116, 81, 147, 108, 118, 107, 148, 121, 147, 116, 0, 148, 140, 108, 118, 107, 148, 114, 117, 98, 3, 0, 116, 0, 148, 140, 108, 118, 107, 148, 121, 97, 116, 140, 108, 118, 107, 148, 109, 116, 108, 118, 140, 107, 148, 109, 116, 108, 118, 140, 107, 148, 109, 108, 117, 102 }; 
      
        byte[] parameter_list = { 2, 2 };
        byte return_type = 2;
        bool need_storage = true;
        string name = "AdditionContractExample";
        string version = "1";
        string author = "chris";
        string email = "chris@neo.org";
        string description = "DescriptionHere";
      
        Contract.Migrate(script, parameter_list, return_type, need_storage, name, version, author, email, description);
          }

    }
}
```



[Back](../Contract.md)