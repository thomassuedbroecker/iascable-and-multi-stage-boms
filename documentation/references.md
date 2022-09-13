# References

### 1. [Bill of Materials YAML reference](https://github.com/cloud-native-toolkit/automation-solutions#bill-of-materials-yaml-reference)

Here's the schema of how a bill of materals `bom.yaml` should be constructed:

- `apiVersion`: `cloud.ibm.com/v1alpha1`
- `kind`: `BillOfMaterial`
- `metadata`: BOM metadatas
- `metadata.name`: Unique BOM identifier, e.g. `110-vpc-openshift`
- `metadata.labels`: BOM labels
- `metadata.labels.type`: BOM type, one of: `infrastructure|software`
- `metadata.labels.platform`: Cloud Platform if BOM is platform specific, one of: `ibm|azure|aws`
- `metadata.labels.code`: BOM 3 digits unique BOM code
- `metadata.annotations`: BOM anotations
- `metadata.annotations.displayName`: BOM plain text name
- `metadata.annotations.description`: BOM description
- `spec`: BOM specifications
- `spec.modules`: **List** of modules referenced by this BOM
- `spec.modules.name`: Module name
- `spec.modules.alias`: Module alias (to be used to reference this module within the BOM)
- `spec.modules.variables`: **List** of module variables to set for this BOM
- `spec.modules.variables.name`: Variable name
- `spec.modules.dependencies`: **List** of module dependencies
- `spec.modules.dependencies.name`: Module name
- `spec.modules.dependencies.ref`: Module reference (alias) if dependent modules appears more than once in the BOM (or generated terraform)

### 2. Reference for [credentials.template](https://github.com/cloud-native-toolkit/iascable/blob/main/credentials.template)

The template `credentials` file needs to be in the `output` folder after you have applied the `iascable` command.

```sh
# Add the values for the Credentials to access the IBM Cloud
# Instructions to access this information can be found in the README.MD
classic.username=""
classic.api.key=""
ibmcloud.api.key=""
# Authentication to OCP can either be performed with username/password or token
# If token is provided it will take precedence
login.user=""
login.password=""
login.token=""
server.url=""
```