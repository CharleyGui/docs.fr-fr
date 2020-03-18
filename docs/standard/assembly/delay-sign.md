---
title: Temporiser la signature d’un assembly
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
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733162"
---
# <a name="delay-sign-an-assembly"></a>Temporiser la signature d’un assembly

Une organisation peut avoir une paire de clés étroitement surveillée que les développeurs ne peuvent pas accéder sur une base quotidienne. La clé publique est souvent disponible, mais l’accès à la clé privée est limité à quelques personnes. Lors du développement d’assemblys avec des noms forts, chaque assembly qui référence l’assembly cible avec nom fort contient le jeton de la clé publique utilisée pour affecter un nom fort à l’assembly cible. La clé publique doit donc être disponible pendant le processus de développement.

Vous pouvez utiliser la signature retardée ou partielle au moment de la construction pour réserver de l’espace dans le fichier portable exécutable (PE) pour la signature du nom fort, mais reporter la signature réelle jusqu’à une étape ultérieure, généralement juste avant l’expédition de l’assemblage.

Pour retarder le signe d’une assemblée :

1. Obtenez la partie clé publique de la paire clé de l’organisation qui fera la signature éventuelle. Typiquement, cette clé est sous la forme d’un fichier *.snk,* qui peut être créé à l’aide [de l’outil Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) fourni par le Windows SDK.

2. Annotez le code source de l’assembly avec deux attributs personnalisés de <xref:System.Reflection> :

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, qui passe le nom du fichier contenant la clé publique en tant que paramètre à son constructeur.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, ce qui indique que la signature de retard est utilisée en passant **vrai** comme un paramètre à son constructeur.

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

     L’exemple suivant éteint la vérification d’une assemblée appelée *myAssembly.dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Pour désactiver la vérification sur les plateformes où vous ne pouvez pas exécuter l’outil Strong Name, telles que les microprocesseurs ARM (Advanced RISC Machine), utilisez l’option **–Vk** pour créer un fichier de Registre. Importez le fichier de Registre dans le Registre sur l’ordinateur sur lequel vous souhaitez désactiver la vérification. L’exemple suivant crée un fichier de Registre pour `myAssembly.dll`.

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   Avec l’option **'Vr** ou **'Vk',** vous pouvez en option inclure un fichier *.snk* pour la signature de clés de test.

   > [!WARNING]
   > Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.

   > [!NOTE]
   > Si vous utilisez la temporisation de signature lors du développement avec Visual Studio sur un ordinateur 64 bits, et que vous compilez un assembly pour **Any CPU**, vous devrez peut-être appliquer deux fois l’option **-Vr**. (Dans Visual Studio, **tout processeur** est une valeur de la propriété de construction De la cible **de plate-forme;** lorsque vous compilez à partir de la ligne de commande, c’est la valeur par défaut.) Pour exécuter votre application à partir de la ligne de commande ou de File Explorer, utilisez la version 64 bits de la [Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md) pour appliquer l’option **-Vr** à l’assemblage. Pour charger l’assembly dans Visual Studio au moment du design (par exemple, si l’assembly contient des composants utilisés par d’autres assemblys dans votre application), utilisez la version 32 bits de l’outil Strong Name. Ceci s’explique par le fait que le compilateur juste-à-temps (JIT) compile l’assembly en code natif 64 bits quand l’assembly est exécuté à partir de la ligne de commande, et en code natif 32 bits quand l’assembly est chargé dans l’environnement au moment du design.

5. Vous soumettez l’assembly ultérieurement, généralement juste avant sa livraison, à l’Autorité de signature de votre organisation pour la signature réelle de nom fort en utilisant l’option **–R** avec l’outil Strong Name.

   L’exemple suivant signe une assemblée appelée *myAssembly.dll* avec un nom fort en utilisant la paire de clés *sgKey.snk.*

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Voir aussi

- [Créer des assemblys](create.md)
- [Guide pratique pour créer une paire de clés publique/privée](create-public-private-key-pair.md)
- [Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md)
