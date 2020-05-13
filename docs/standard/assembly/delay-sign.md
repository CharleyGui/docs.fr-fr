---
title: Temporiser la signature d’un assembly
description: Cet article décrit la signature différée ou partielle, qui réserve de l’espace dans le fichier PE pour la signature de nom fort, mais diffère la signature réelle.
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 7b5c8c8463fdc573782fa457bf5671c72a7e25f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378503"
---
# <a name="delay-sign-an-assembly"></a>Temporiser la signature d’un assembly

Une organisation peut avoir une paire de clés étroitement protégée que les développeurs ne peuvent pas accéder quotidiennement. La clé publique est souvent disponible, mais l’accès à la clé privée est limité à quelques personnes. Lors du développement d’assemblys avec des noms forts, chaque assembly qui référence l’assembly cible avec nom fort contient le jeton de la clé publique utilisée pour affecter un nom fort à l’assembly cible. La clé publique doit donc être disponible pendant le processus de développement.

Vous pouvez utiliser la signature différée ou partielle au moment de la génération pour réserver de l’espace dans le fichier exécutable portable (PE) pour la signature de nom fort, mais différer la signature réelle jusqu’à une étape ultérieure, généralement juste avant la livraison de l’assembly.

Pour différer la signature d’un assembly :

1. Récupérez la partie clé publique de la paire de clés de l’organisation qui effectuera la signature finale. En général, cette clé se présente sous la forme d’un fichier *. snk* , qui peut être créé à l’aide de l' [outil Strong Name Tool (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) fourni par le SDK Windows.

2. Annotez le code source de l’assembly avec deux attributs personnalisés de <xref:System.Reflection> :

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, qui passe le nom du fichier contenant la clé publique en tant que paramètre à son constructeur.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, qui indique que la signature différée est utilisée en passant **true** comme paramètre à son constructeur.

   Par exemple :

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. Le compilateur insère la clé publique dans le manifeste d’assembly et réserve de l’espace dans le fichier PE pour la signature de nom fort complète. La clé publique réelle doit être stockée lors de la génération de l’assembly, de sorte que d’autres assemblys référençant cet assembly puissent obtenir la clé à stocker dans leur propre référence d’assembly.

4. Étant donné que l’assembly n’a pas de signature de nom fort valide, la vérification de cette signature doit être désactivée. Vous pouvez pour cela utiliser l’option **–Vr** avec l’outil Strong Name.

     L’exemple suivant désactive la vérification d’un assembly appelé *myAssembly. dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Pour désactiver la vérification sur les plateformes où vous ne pouvez pas exécuter l’outil Strong Name, telles que les microprocesseurs ARM (Advanced RISC Machine), utilisez l’option **–Vk** pour créer un fichier de Registre. Importez le fichier de Registre dans le Registre sur l’ordinateur sur lequel vous souhaitez désactiver la vérification. L’exemple suivant crée un fichier de Registre pour `myAssembly.dll`.

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   Avec l’option **– VR** ou **– VK** , vous pouvez éventuellement inclure un fichier *. snk* pour la signature de la clé de test.

   > [!WARNING]
   > Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.

   > [!NOTE]
   > Si vous utilisez la temporisation de signature lors du développement avec Visual Studio sur un ordinateur 64 bits, et que vous compilez un assembly pour **Any CPU**, vous devrez peut-être appliquer deux fois l’option **-Vr**. (Dans Visual Studio, **toute UC** est une valeur de la propriété de build cible de la **plateforme** ; quand vous compilez à partir de la ligne de commande, il s’agit de la valeur par défaut.) Pour exécuter votre application à partir de la ligne de commande ou de l’Explorateur de fichiers, utilisez la version 64 bits de [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md) pour appliquer l’option **-VR** à l’assembly. Pour charger l’assembly dans Visual Studio au moment du design (par exemple, si l’assembly contient des composants utilisés par d’autres assemblys dans votre application), utilisez la version 32 bits de l’outil Strong Name. Ceci s’explique par le fait que le compilateur juste-à-temps (JIT) compile l’assembly en code natif 64 bits quand l’assembly est exécuté à partir de la ligne de commande, et en code natif 32 bits quand l’assembly est chargé dans l’environnement au moment du design.

5. Vous soumettez l’assembly ultérieurement, généralement juste avant sa livraison, à l’Autorité de signature de votre organisation pour la signature réelle de nom fort en utilisant l’option **–R** avec l’outil Strong Name.

   L’exemple suivant signe un assembly appelé *myAssembly. dll* avec un nom fort à l’aide de la paire de clés *sgKey. snk* .

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Voir aussi

- [Créer des assemblys](create.md)
- [Guide pratique pour créer une paire de clés publique/privée](create-public-private-key-pair.md)
- [SN. exe (outil Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md)
