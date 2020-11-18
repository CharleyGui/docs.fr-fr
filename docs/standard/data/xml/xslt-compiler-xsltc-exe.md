---
title: XSLT Compiler (xsltc.exe)
ms.date: 03/30/2017
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: cfeebc3ac0c0259c975439dc93c3c5f003b60c40
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818321"
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT Compiler (xsltc.exe)
Le compilateur XSLT (xsltc.exe) compile des feuilles de style XSLT et génère un assembly. La feuille de style compilée peut être passée directement dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>. Vous ne pouvez pas générer d'assemblys signés avec xsltc.exe.  
  
 L’outil xsltc.exe est inclus dans Visual Studio. Pour plus d’informations, consultez les [Téléchargements Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Description|  
|--------------|-----------------|  
|`sourceFile`|Spécifie le nom de la feuille de style. La feuille de style doit être un fichier local ou se trouver sur l'intranet.|  
  
## <a name="options"></a>Options  
  
|Option|Description|  
|------------|-----------------|  
|`/c[lass]:` `name`|Définit le nom de la classe pour la feuille de style suivante. Le nom de la classe peut être un nom qualifié complet.<br /><br /> Le nom de la classe est par défaut celui de la feuille de style. Par exemple, si la feuille de style customers.xsl est compilée, le nom de la classe par défaut est customers.|  
|`/debug[`+&#124;-`]`|Spécifie s'il faut générer des informations de débogage.<br /><br /> Si vous spécifiez `+` ou `/debug`, le compilateur génère des informations de débogage et les place dans un fichier (PDB) de la base de données du programme. Le nom du fichier PDB généré est `assemblyName`.pdb.<br /><br /> Si vous spécifiez `-`, qui est en vigueur si vous ne spécifiez pas `/debug`, aucune information de débogage n'est créée. Un assembly retail est généré. **Remarque :** la compilation en mode débogage peut affecter considérablement les performances de XSLT.|  
|`/help`|Affiche la syntaxe et les options de commande de l'outil.|  
|`/nologo`|Supprime l'affichage du message de copyright du compilateur.|  
|`/platform:` `string`|Spécifie les plateformes sur lesquelles l'assembly peut s'exécuter. Les valeurs de plateforme valides sont décrites ci-dessous :<br /><br /> `x86` compile votre assembly pour qu'il soit exécuté par le CLR 32 bits x86.<br /><br /> `x64` compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.<br /><br /> Itanium compile votre assembly pour que celui-ci soit exécuté par le CLR 64 bits sur un ordinateur doté d’un processeur Itanium.<br /><br /> `anycpu` compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme. Il s’agit de la valeur par défaut.|  
|`/out:` `assemblyName`|Spécifie le nom de l'assembly qui est produit. Le nom de l'assembly est par défaut celui de la feuille de style principale ou de la première feuille de style s'il y en a plusieurs.<br /><br /> Si la feuille de style contient des scripts, ceux-ci sont enregistrés dans un assembly séparé. Les noms d'assemblys de script sont générés d'après le nom de l'assembly principal. Par exemple, si vous avez spécifié CustOrders.dll comme nom d'assembly, le premier assembly de script est nommé CustOrders_Script1.dll.|  
|`/settings:` `document+-, script+-, DTD+-,`|Spécifie s'il faut autoriser des fonctions `document()`, un script XSLT ou une définition de type de document (DTD) dans la feuille de style.<br /><br /> Le comportement par défaut désactive la prise en charge de la DTD, la fonction `document()` et les scripts.|  
|`@` `file`|Vous permet de spécifier un fichier qui contient les options du compilateur.|  
|`?`|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Notes  
 Les solutions XSLT peuvent être constituées de plusieurs modules de feuilles de style. L'outil xsltc.exe génère des assemblys à partir des feuilles de style. Les assemblys peuvent ensuite être passés dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>. Cela peut permettre de réduire le coût des performances dans certains scénarios de déploiement XSLT.  
  
> [!NOTE]
> Vous devez également inclure l'assembly compilé comme référence dans votre application.  
  
 L’outil xsltc.exe ne valide pas les noms de classe (`/class:`*nom*) ou les noms d’assembly (`/out:`*nom_assembly*). Si les noms ne sont pas valides, le Common Language Runtime lève des erreurs.  
  
## <a name="examples"></a>Exemples  
 La commande suivante compile la feuille de style et crée un assembly nommé booksort.dll.  
  
```console  
xsltc booksort.xsl  
```  
  
 La commande suivante compile la feuille de style et crée un assembly et un fichier PDB nommés respectivement booksort.dll et booksort.pdb.  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 La commande suivante compile une feuille de style qui contient un élément msxsl:script et crée deux assemblys nommés calc.dll et calc_Script1.dll.  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 La commande suivante active le traitement DTD et la prise en charge de script et crée deux assemblys nommés myTest.dll et myTest_Script1.dll.  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 La commande suivante compile deux modules de feuilles de style et crée un assembly unique nommé booksort.dll.  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Procédure : effectuer une transformation XSLT à l’aide d’un assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [Transformations XSLT](xslt-transformations.md)
