---
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 3c02c914a27e6095f8f6bc34e29e2447a1a373e5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065721"
---
# <a name="-link-visual-basic"></a>-Link (Visual Basic)

Fait que le compilateur rend disponible pour le projet en cours de compilation les informations de type COM des assemblys spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-link:fileList  
```

or  

```console
-l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileList`|Obligatoire. Liste délimitée par des virgules des noms de fichiers d’assembly. Si le nom de fichier contient un espace, placez-le entre des guillemets.|  
  
## <a name="remarks"></a>Notes  

 L’option `-link` vous permet de déployer une application qui a des informations de type incorporées. L’application peut ensuite utiliser des types dans un assembly de runtime qui implémentent les informations de type incorporées sans nécessiter une référence à l’assembly de runtime. Si différentes versions de l’assembly de runtime sont publiées, l’application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans devoir être recompilée. Pour un exemple, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md).  
  
 L’utilisation de l’option `-link` est particulièrement utile quand vous travaillez avec COM Interop. Vous pouvez incorporer des types COM afin que votre application ne nécessite plus un assembly PIA (Primary Interop Assembly) sur l’ordinateur cible. L’option `-link` indique au compilateur d’incorporer les informations de type COM provenant de l’assembly Interop référencé dans le code compilé résultant. Le type COM est identifié par la valeur du CLSID (GUID). Par conséquent, votre application peut s’exécuter sur un ordinateur cible où les mêmes types COM ont été installés avec les mêmes valeurs de CLSID. Les applications qui automatisent Microsoft Office sont un bon exemple. Étant donné que les applications comme Office gardent habituellement la même valeur de CLSID à travers différentes versions, votre application peut utiliser les types COM référencés dès lors que le .NET Framework 4 ou ultérieur est installé sur l’ordinateur cible, et que votre application utilise les méthodes, propriétés ou événements qui sont inclus dans les types COM référencés.  
  
 L’option `-link` incorpore seulement les interfaces, les structures et les délégués. L’incorporation de classes COM n’est pas prise en charge.  
  
> [!NOTE]
> Quand vous créez une instance d’un type COM incorporé dans votre code, vous devez créer l’instance à l’aide de l’interface appropriée. Une tentative de création d’une instance d’un type COM incorporé à l’aide de la coclasse provoque une erreur.  
  
 Pour définir l’option `-link` dans Visual Studio, ajoutez une référence d’assembly et définissez la propriété `Embed Interop Types` sur **true**. La valeur par défaut pour la propriété `Embed Interop Types` est **false**.  
  
 Si vous liez à un assembly COM (Assembly A) qui référence lui-même un autre assembly COM (Assembly B), vous devez également lier à l’Assembly B si une des conditions suivantes est vraie :  
  
- Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.  
  
- Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.  
  
 Utilisez [-LIBPATH](libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs références d’assembly.  
  
 À l’instar de l’option [de compilateur-Reference](reference.md) , l' `-link` option de compilateur utilise le fichier réponse Vbc. rsp, qui référence les assemblys .NET Framework fréquemment utilisés. Utilisez l’option [de compilateur-noconfig](noconfig.md) si vous ne souhaitez pas que le compilateur utilise le fichier Vbc. rsp.  
  
 La forme abrégée de `-link` est `-l`.  
  
## <a name="generics-and-embedded-types"></a>Types génériques et imbriqués  

 Les sections suivantes décrivent les limitations de l’utilisation de types génériques dans les applications qui incorporent des types interop.  
  
### <a name="generic-interfaces"></a>Interfaces génériques  

 Vous ne pouvez pas utiliser des interfaces génériques incorporées depuis un assembly d’interopérabilité. Cela est illustré par l'exemple suivant.  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Types ayant des paramètres génériques  

 Vous ne pouvez pas utiliser des types qui ont un paramètre générique dont le type est incorporé depuis un assembly d’interopérabilité si ce type provient d’un assembly externe. Cette restriction ne s’applique pas aux interfaces. Prenons l’exemple de l’interface <xref:Microsoft.Office.Interop.Excel.Range> qui est définie dans l’assembly <xref:Microsoft.Office.Interop.Excel>. Si une bibliothèque incorpore les types interop de l’assembly <xref:Microsoft.Office.Interop.Excel> et expose une méthode qui retourne un type générique qui a un paramètre dont le type est l’interface <xref:Microsoft.Office.Interop.Excel.Range>, cette méthode doit retourner une interface générique, comme dans l’exemple de code suivant.  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 Dans l’exemple suivant, le code client peut appeler la méthode qui retourne l’interface générique <xref:System.Collections.IList> sans erreur.  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>Exemple  

 La ligne de commande suivante compile le fichier source `OfficeApp.vb` et les assemblys de référence à partir de `COMData1.dll` et `COMData2.dll` à produire `OfficeApp.exe` .  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../../../standard/assembly/embed-types-visual-studio.md)
- [-Reference (Visual Basic)](reference.md)
- [-noconfig](noconfig.md)
- [-libpath](libpath.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Présentation de COM Interop](../../programming-guide/com-interop/introduction-to-com-interop.md)
