---
title: Temporisation de signature d'un assembly
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb055285af7365536f7e1ad7c7d9290e51be50db
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832865"
---
# <a name="delay-signing-an-assembly"></a>Temporisation de signature d'un assembly
Une entreprise peut avoir une paire de clés protégées auxquelles les développeurs n’ont pas accès tous les jours. La clé publique est souvent disponible, mais l’accès à la clé privée est limité à quelques personnes. Lors du développement d’assemblys avec des noms forts, chaque assembly qui référence l’assembly cible avec nom fort contient le jeton de la clé publique utilisée pour affecter un nom fort à l’assembly cible. La clé publique doit donc être disponible pendant le processus de développement.  
  
 Vous pouvez utiliser la signature différée ou partielle au moment de la génération pour réserver de l’espace dans le fichier exécutable portable (PE) pour la signature de nom fort, mais différer la signature à une étape ultérieure (généralement juste avant de livrer l’assembly).  
  
 Les étapes suivantes décrivent le processus permettant de différer la signature d’un assembly :  
  
1. Obtenez la partie clé publique de la paire de clés auprès de la société qui effectuera la signature. En règle générale, cette clé se présente sous la forme d’un fichier .snk, qui peut être créé à l’aide de l’[outil Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) fourni dans le kit de développement logiciel (SDK) Windows.  
  
2. Annotez le code source de l’assembly avec deux attributs personnalisés de <xref:System.Reflection> :  
  
    - <xref:System.Reflection.AssemblyKeyFileAttribute>, qui passe le nom du fichier contenant la clé publique en tant que paramètre à son constructeur.  
  
    - <xref:System.Reflection.AssemblyDelaySignAttribute>, qui indique l’utilisation de la temporisation de signature en passant **true** comme paramètre à son constructeur. Par exemple :  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. Le compilateur insère la clé publique dans le manifeste d’assembly et réserve de l’espace dans le fichier PE pour la signature de nom fort complète. La clé publique réelle doit être stockée lors de la génération de l’assembly, de sorte que d’autres assemblys référençant cet assembly puissent obtenir la clé à stocker dans leur propre référence d’assembly.  
  
4. Étant donné que l’assembly n’a pas de signature de nom fort valide, la vérification de cette signature doit être désactivée. Vous pouvez pour cela utiliser l’option **–Vr** avec l’outil Strong Name.  
  
     L’exemple suivant désactive la vérification pour un assembly nommé `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Pour désactiver la vérification sur les plateformes où vous ne pouvez pas exécuter l’outil Strong Name, telles que les microprocesseurs ARM (Advanced RISC Machine), utilisez l’option **–Vk** pour créer un fichier de Registre. Importez le fichier de Registre dans le Registre sur l’ordinateur sur lequel vous souhaitez désactiver la vérification. L’exemple suivant crée un fichier de Registre pour `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Avec l’option **–Vr** ou **–Vk**, vous pouvez éventuellement inclure un fichier .snk pour la signature de clé test.  
  
    > [!WARNING]
    > Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.
  
    > [!NOTE]
    >  Si vous utilisez la temporisation de signature lors du développement avec Visual Studio sur un ordinateur 64 bits, et que vous compilez un assembly pour **Any CPU**, vous devrez peut-être appliquer deux fois l’option **-Vr**. (Dans Visual Studio, **Any CPU** est une valeur de la propriété de build **Plateforme cible** ; quand vous compilez à partir de la ligne de commande, il s’agit de la valeur par défaut.) Pour exécuter votre application à partir de la ligne de commande ou de l’Explorateur de fichiers, utilisez la version 64 bits de [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pour appliquer l’option **-Vr** à l’assembly. Pour charger l’assembly dans Visual Studio au moment du design (par exemple, si l’assembly contient des composants utilisés par d’autres assemblys dans votre application), utilisez la version 32 bits de l’outil Strong Name. Ceci s’explique par le fait que le compilateur juste-à-temps (JIT) compile l’assembly en code natif 64 bits quand l’assembly est exécuté à partir de la ligne de commande, et en code natif 32 bits quand l’assembly est chargé dans l’environnement au moment du design.  
  
5. Vous soumettez l’assembly ultérieurement, généralement juste avant sa livraison, à l’Autorité de signature de votre organisation pour la signature réelle de nom fort en utilisant l’option **–R** avec l’outil Strong Name.  
  
     L’exemple suivant signe un assembly nommé `myAssembly.dll` avec un nom fort à l’aide de la paire de clés `sgKey.snk`.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)
- [Guide pratique pour créer une paire de clés publique/privée](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (outil Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
