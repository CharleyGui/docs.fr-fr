---
title: Tlbimp.exe (Type Library Importer)
description: Utilisez Tlbimp.exe, l’importateur de bibliothèques de types. Cet outil convertit les définitions de type trouvées dans une bibliothèque de types COM en définitions équivalentes dans un assembly CLR.
ms.date: 03/30/2017
helpviewer_keywords:
- type libraries [.NET Framework], importing
- importing type library
- Tlbimp.exe
- type definition conversion
- Type Library Importer
- type libraries
- converting type definitions
ms.assetid: ec0a8d63-11b3-4acd-b398-da1e37e97382
ms.openlocfilehash: 4c2cddd78e14d1ae0b04bab07b57fe0ce0f627ca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543366"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Type Library Importer)
L''importateur de bibliothèques de types convertit les définitions de types présentes dans une bibliothèque de types COM en définitions équivalentes dans un assembly de Common Language Runtime. Le résultat de Tlbimp.exe est un fichier binaire (un assembly) qui contient les métadonnées de runtime pour les types définis dans la bibliothèque de types d'origines. Vous pouvez examiner ce fichier à l’aide d’outils comme [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Argument|Description|  
|--------------|-----------------|  
|*tlbFile*|Nom d'un fichier qui contient une bibliothèque de types COM.|  
  
|Option|Description|  
|------------|-----------------|  
|**/asmversion:** *versionnumber*|Spécifie le numéro de version de l'assembly à produire. Spécifiez *versionnumber* au format *major.minor.build.revision*.|  
|**/Company :**`companyinformation`|Ajoute les informations de l'entreprise à l'assembly de sortie.|  
|**/Copyright :**`copyrightinformation`|Ajoute les informations de copyright à l'assembly de sortie. Ces informations peuvent être affichées dans la boîte de dialogue **Propriétés du fichier** de l’assembly.|  
|**/delaysign**|Indique à Tlbimp.exe de signer l'assembly résultant avec un nom fort à l'aide d'une signature différée. Vous devez spécifier cette option avec l’option **/keycontainer:**, **/keyfile:** ou **/publickey:**. Pour plus d’informations sur le processus de signature différée, consultez [Temporisation de signature d’un assembly](../../standard/assembly/delay-sign.md).|  
|**/Help**|Affiche la syntaxe et les options de commande de l'outil.|  
|**/keycontainer:** *containername*|Signe l’assembly obtenu avec un nom fort en utilisant la paire de clés publique/privée présente dans le conteneur de clé spécifié par *containername*.|  
|**/keyfile:** *filename*|Signe l’assembly obtenu avec un nom fort en utilisant la paire de clés publique/privée officielle de l’éditeur présente dans *filename*.|  
|**/machine :**`machinetype`|Crée un assembly qui cible le type de l'ordinateur spécifié (microprocesseur). Types d'ordinateur pris en charge : x86, x64, Itanium, et agnostique.|  
|**/namespace:** *namespace*|Spécifie l'espace de noms dans lequel produire l'assembly.|  
|**/noclassmembers**|Empêche Tlbimp.exe d'ajouter des membres aux classes. Cela évite une <xref:System.TypeLoadException> potentielle.|  
|**/nologo**|Supprime l'affichage de la bannière de démarrage Microsoft.|  
|**/out :** *NomFichier*|Spécifie le nom du fichier de sortie, de l'assembly et de l'espace de noms dans lesquels écrire les définitions de métadonnées. L’option **/out** n’a aucun effet sur l’espace de noms de l’assembly si la bibliothèque de types spécifie l’attribut personnalisé IDL (Interface Definition Language) qui contrôle explicitement l’espace de noms de l’assembly. Si vous ne spécifiez pas cette option, Tlbimp.exe écrit les métadonnées dans un fichier portant le même nom que la bibliothèque de types effective définie dans le fichier d’entrée, et lui assigne une extension .dll. Si le fichier de sortie porte le même nom que le fichier d'entrée, l'outil génère une erreur pour empêcher le remplacement de la bibliothèque de types.|  
|**/Primary**|Produit un assembly PIA (Primary Interop Assembly) pour la bibliothèque de types spécifiée. Des informations sont ajoutées à l'assembly pour indiquer qu'il a été produit par l'éditeur de la bibliothèque de types. En spécifiant un assembly PIA, vous différenciez l'assembly d'un éditeur des autres assemblys créés à partir de la bibliothèque de types à l'aide de Tlbimp.exe. Vous devez utiliser uniquement l’option **/primary** si vous êtes l’éditeur de la bibliothèque de types que vous importez avec Tlbimp.exe. Notez que vous devez signer un assembly PIA (Primary Interop Assembly) avec un [nom fort](../../standard/assembly/strong-named.md). Pour plus d’informations, consultez [Assemblys PIA (Primary Interop Assembly)](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/Product :**`productinformation`|Ajoute les informations produit à l'assembly de sortie. Ces informations peuvent être affichées dans la boîte de dialogue **Propriétés du fichier** de l’assembly.|  
|**/ProductVersion :**`productversioninformation`|Ajoute les informations de version du produit à l'assembly de sortie. Il n'existe aucune restriction de format. Ces informations peuvent être affichées dans la boîte de dialogue **Propriétés du fichier** de l’assembly.|  
|**/publickey:** *filename*|Spécifie le fichier contenant la clé publique à utiliser pour signer l'assembly résultant. Si vous spécifiez l’option **/keyfile:** ou **/keycontainer:** au lieu de **/publickey:**, Tlbimp.exe génère la clé publique à partir de la paire de clés publique/privée fournie avec **/keyfile:** ou **/keycontainer:**. L’option **/publickey:** prend en charge les scénarios de clé de test et de signature différée. Le fichier est au format généré par Sn.exe. Pour plus d’informations, consultez l’option **-p** de Sn.exe dans l’[outil Strong Name (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/reference:** *filename*|Spécifie le fichier d'assembly à utiliser pour résoudre les références aux types définis en dehors de la bibliothèque de types en cours. Si vous ne spécifiez pas l’option **/reference**, Tlbimp.exe importe automatiquement de manière récursive les bibliothèques de types externes que la bibliothèque de types importée référence. Si vous spécifiez l’option **/reference**, l’outil essaie de résoudre les types externes des assemblys référencés avant d’importer d’autres bibliothèques de types.|  
|**/silence:** `warningnumber`|Supprime l'affichage de l'avertissement spécifié. Cette option ne peut pas être utilisée avec **/silent**.|  
|**/Silent**|Supprime l'affichage des messages indiquant la réussite des opérations. Cette option ne peut pas être utilisée avec **/silence**.|  
|**/strictref**|N’importe pas de bibliothèque de types si l’outil ne peut pas résoudre toutes les références au sein de l’assembly actuel, des assemblys spécifiés avec l’option **/reference** ou des assemblys PIA (Primary Interop Assembly).|  
|**/strictref:nopia**|Similaire à **/strictref**, mais ignore les assemblys PIA.|  
|**/sysarray**|Indique à l’outil d’importer un SafeArray COM comme type <xref:System.Array> managé.|  
|**/tlbreference:** *filename*|Spécifie le fichier bibliothèque de types à utiliser pour résoudre des références de bibliothèque de types sans consulter le Registre.<br /><br /> Notez que cette option ne charge pas certains formats de bibliothèque de types plus anciens.  Toutefois, vous pouvez toujours charger les formats de bibliothèque de types plus anciens par le biais du Registre ou du répertoire actif.|  
|**/trademark:** `trademarkinformation`|Ajoute les informations de marque commerciale à l'assembly de sortie. Ces informations peuvent être affichées dans la boîte de dialogue **Propriétés du fichier** de l’assembly.|  
|**/transform:** *transformname*|Transforme des métadonnées comme spécifié par le paramètre *transformname*.<br /><br /> Spécifiez **dispret** pour le paramètre *transformname* pour transformer les paramètres [out, retval] des méthodes sur des interfaces de dispatch uniquement (dispinterfaces) en valeurs de retour.<br /><br /> Pour plus d'informations sur cette option, consultez les exemples plus loin dans cette rubrique.|  
|**/unsafe**|Produit des interfaces sans contrôles de sécurité .NET Framework. L'appel d'une méthode ainsi exposée peut poser des problèmes de sécurité. Vous ne devez pas utiliser cette option à moins d'être bien conscient des risques liés à l'exposition d'un tel code.|  
|**/verbose**|Spécifie le mode documenté, qui affiche des informations supplémentaires sur la bibliothèque de types importée.|  
|**/VariantBoolFieldToBool**|Convertit les champs `VARIANT_BOOL` en structures dans <xref:System.Boolean>.|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
> [!NOTE]
> Les options de ligne de commande de Tlbimp.exe ne font pas l'objet d'une distinction minuscules/majuscules et peuvent être fournies dans n'importe quel ordre. Il vous suffit de spécifier les éléments de l'option nécessaires à son identification de manière unique. Par conséquent, **/n** équivaut à **/nologo** et **/ou:** *outfile.dll* équivaut à **/out:** *outfile.dll*.  
  
## <a name="remarks"></a>Notes  
 Tlbimp.exe effectue d'un seul tenant les conversions sur la totalité d'une bibliothèque de types. Vous ne pouvez pas utiliser cet outil dans le but de générer des informations de type pour un sous-ensemble de types définis dans une bibliothèque de types unique.  
  
 Il est souvent utile ou nécessaire d’assigner des [noms forts](../../standard/assembly/strong-named.md) aux assemblys. Par conséquent, Tlbimp.exe comprend des options permettant de fournir les informations nécessaires pour générer des assemblys portant un nom fort. Les options **/keyfile:** et **/keycontainer:** permettent de signer les assemblys avec des noms forts. Par conséquent, il est logique de fournir uniquement une seule de ces options à la fois.  
  
 Vous pouvez spécifier plusieurs assemblys de référence en utilisant l’option **/reference** plusieurs fois.

 En raison de la façon dont Tlbimp.exe génère des assemblys, il n’est pas possible de rediriger un assembly vers une autre version `mscorlib`. Par exemple, si vous souhaitez générer un assembly qui cible .NET Framework 2.0, vous devez utiliser le fichier Tlbimp.exe fourni avec le kit SDK .NET Framework 2.0/3.0/3.5. Pour cibler .NET Framework 4.x, vous devez utiliser le Tlbimp.exe fourni avec un kit SDK .NET Framework 4.x.

 Un ID de ressource peut être ajouté de manière facultative à un fichier bibliothèque de types lors de l'importation d'une bibliothèque de types à partir d'un module contenant plusieurs bibliothèques de types. Tlbimp.exe peut localiser ce fichier uniquement s'il se trouve dans le répertoire en cours, ou si vous spécifiez le chemin d'accès complet. Consultez l'exemple décrit plus loin dans cette rubrique.  
  
## <a name="examples"></a>Exemples  
 La commande suivante génère un assembly dont le nom est identique à celui de la bibliothèque de types présente dans `myTest.tlb` et qui porte l'extension .dll.  
  
```console  
tlbimp myTest.tlb
```  
  
 La commande suivante génère un assembly portant le nom `myTest.dll`.  
  
```console  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 La commande suivante génère un assembly avec le même nom que celui de la bibliothèque de types spécifiée par `MyModule.dll\1` et avec l’extension .dll. `MyModule.dll\1` doit se trouver dans le répertoire actif.  
  
```console  
tlbimp MyModule.dll\1  
```  
  
 La commande suivante génère un assembly portant le nom `myTestLib.dll` pour la bibliothèque de types `TestLib.dll`. L’option **/transform:dispret** transforme tous les paramètres [out, retval] des méthodes sur les dispinterfaces dans la bibliothèque de types en valeur de retour dans la bibliothèque managée.  
  
```console  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Dans l'exemple précédent, la bibliothèque de types `TestLib.dll` contient une méthode dispinterface nommée `SomeMethod` qui retourne void et a un paramètre [out, retval]. Le code suivant est la signature de méthode de bibliothèque de types d'entrées de `SomeMethod` dans `TestLib.dll`.  
  
```cpp  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Si vous spécifiez l’option **/transform:dispret**, Tlbimp.exe transforme le paramètre `[out, retval]` de `SomeMethod` en valeur de retour `bool`. L’exemple de code suivant est la signature de méthode que génère Tlbimp.exe pour `SomeMethod` dans la bibliothèque managée `myTestLib.dll` quand l’option **/transform:dispret** est spécifiée.  
  
```csharp  
bool SomeMethod();  
```  
  
 Si vous utilisez Tlbimp.exe pour générer une bibliothèque managée pour `TestLib.dll` sans spécifier l’option **/transform:dispret**, l’outil génère la signature de méthode suivante pour `SomeMethod` dans la bibliothèque managée `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Tlbexp.exe (exportateur de bibliothèques de types)](tlbexp-exe-type-library-exporter.md)
- [Importation d'une bibliothèque de types sous la forme d'un assembly](../interop/importing-a-type-library-as-an-assembly.md)
- [Récapitulatif de la conversion d’une bibliothèque de types en assembly](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (Désassembleur IL)](ildasm-exe-il-disassembler.md)
- [Sn.exe (outil Strong Name Tool)](sn-exe-strong-name-tool.md)
- [Assemblys avec noms forts](../../standard/assembly/strong-named.md)
- [Attributs d’importation de bibliothèques de types dans les assemblys d’interopérabilité](/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Invites de commandes](developer-command-prompt-for-vs.md)
