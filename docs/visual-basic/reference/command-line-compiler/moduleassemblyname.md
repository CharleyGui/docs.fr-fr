---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 99f2b9d65f3c2a128e026666c5efb384e22643f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403146"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Spécifie le nom de l’assembly dont ce module doit faire partie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`assembly_name`|Nom de l'assembly dont ce module fera partie.|  
  
## <a name="remarks"></a>Notes  
 Le compilateur traite l' `-moduleassemblyname` option uniquement si l' `-target:module` option a été spécifiée. Le compilateur crée alors un module. Le module créé par le compilateur est valide uniquement pour l’assembly spécifié avec l' `-moduleassemblyname` option. Si vous placez le module dans un assembly différent, des erreurs d’exécution se produisent.  
  
 L' `-moduleassemblyname` option est requise uniquement lorsque les conditions suivantes sont remplies :  
  
- Un type de données dans le module a besoin d’accéder à un `Friend` type dans un assembly référencé.  
  
- L’assembly référencé a accordé un accès d’assembly friend à l’assembly dans lequel le module sera généré.  
  
 Pour plus d’informations sur la création d’un module, consultez [-target (Visual Basic)](target.md). Pour plus d’informations sur les assemblys friend, consultez [assemblys friend](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> L' `-moduleassemblyname` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement quand vous compilez à partir d’une invite de commandes.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : générer un assembly multifichier](../../../framework/app-domains/build-multifile-assembly.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-cible (Visual Basic)](target.md)
- [-main](main.md)
- [-Reference (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Assemblys friend](../../../standard/assembly/friend.md)
