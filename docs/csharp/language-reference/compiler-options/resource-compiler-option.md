---
description: -resource (Options du compilateur C#)
title: -resource (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 1e2de095b460b684fb06faf46731283a1304906e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465687"
---
# <a name="-resource-c-compiler-options"></a>-resource (Options du compilateur C#)
Incorpore la ressource spécifiée dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Fichier de ressources .NET que vous souhaitez incorporer dans le fichier de sortie.  
  
 `identifier` (facultatif)  
 Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.  
  
 `accessibility-modifier` (facultatif)  
 Accessibilité de la ressource : publique ou privée. La valeur par défaut est public.  
  
## <a name="remarks"></a>Remarques  
 Utilisez [-linkresource](./linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.  
  
 Par défaut, les ressources sont publiques dans l’assembly quand elles sont créées à l’aide du compilateur C#. Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`. Aucune accessibilité autre `public` ou `private` n’est autorisée.  
  
 Si `filename` est un fichier de ressources .net créé, par exemple par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de l' <xref:System.Resources> espace de noms. Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.  
  
 **-res** est la forme abrégée de **-resource**.  
  
 L’ordre des ressources dans le fichier de sortie est déterminé par l’ordre spécifié sur la ligne de commande.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ajoutez un fichier de ressources à votre projet.  
  
2. Sélectionnez le fichier que vous souhaitez incorporer dans l’**Explorateur de solutions**.  
  
3. Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.  
  
4. Définissez **Action de génération ** sur **Ressource incorporée**.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
