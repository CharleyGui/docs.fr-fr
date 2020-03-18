---
title: -target:appcontainerexe (Options du compilateur C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204523"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (Options du compilateur C#)
Si vous utilisez l’option du compilateur **-target:appcontainerexe**, le compilateur crée un fichier exécutable Windows (.exe) qui doit être exécuté dans un conteneur d’application. Cette option est équivalente à [-target:winexe](./target-winexe-compiler-option.md) mais est conçu pour Windows 8.x Store applications.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Notes   
 Pour exiger que l’application s’exécute dans un conteneur d’application, cette option définit un bit dans le fichier [Portable Executable](/windows/desktop/Debug/pe-format) (PE). Lorsque ce bit est défini, une erreur se produit si la méthode CreateProcess tente de lancer l'exécutable en dehors d'un conteneur d'application.  
  
 À moins que vous utilisiez l’option [-out](./out-compiler-option.md), le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../programming-guide/main-and-command-args/index.md).  
  
 Quand vous spécifiez cette option à une invite de commandes, tous les fichiers jusqu’à l’option **-out** ou **-target** suivante sont utilisés pour créer le fichier exécutable.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Pour définir cette option du compilateur dans l'IDE  
  
1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.  
  
2. Sous l’onglet **Application**, dans la liste **Type de sortie**, choisissez **Application Windows Store**.  
  
     Cette option n’est disponible que pour les modèles d’applications Windows 8.x Store.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a> Exemple  
 La commande suivante compile `filename.cs` dans un fichier exécutable Windows qui peut être exécuté uniquement dans un conteneur d'application.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [-cible (Options compilateur C)](./target-compiler-option.md)
- [-cible:winexe (Options compilateur C)](./target-winexe-compiler-option.md)
- [Options de compilateur C](./index.md)
