---
title: Aspects de la sécurité des assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], security
- signcodes
- names [.NET Framework], assemblies
- strong-named assemblies, security considerations
- signing assemblies
- assemblies [.NET Framework], signing
- granting permissions, assemblies
- assemblies [.NET Framework], strong-named
- names [.NET Framework], strong names
- permissions [.NET Framework], assemblies
- security [.NET Framework], assemblies
- integrity with assemblies
ms.assetid: 1b5439c1-f3d5-4529-bd69-01814703d067
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6f6fa8afe2e4aaea6e9f2b96329542b7fe5292
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607696"
---
# <a name="assembly-security-considerations"></a>Aspects de la sécurité des assemblys
<a name="top"></a>Lorsque vous générez un assembly, vous pouvez spécifier un jeu d’autorisations que l’assembly doit exécuter. L'octroi ou non de certaines autorisations à un assembly repose sur la preuve.  
  
 La preuve est utilisée de deux façons :  
  
- La preuve d’entrée est fusionnée avec la preuve rassemblée par le chargeur afin de constituer un jeu final de preuves utilisé pour la résolution de stratégie. Les méthodes qui utilisent cette sémantique sont **Assembly.Load**, **Assembly.LoadFrom** et **Activator.CreateInstance**.  
  
- La preuve d’entrée est utilisée sans altération comme jeu final de preuves utilisé pour la résolution de stratégie. Les méthodes qui utilisent cette sémantique sont **Assembly.Load(byte[])** et **AppDomain.DefineDynamicAssembly()**.  
  
 Des autorisations facultatives peuvent être accordées par la [stratégie de sécurité](../../../docs/framework/misc/code-access-security-basics.md) définie sur l’ordinateur sur lequel l’assembly s’exécute. Si vous souhaitez que votre code gère toutes les exceptions de sécurité possibles, vous pouvez effectuer l'une des opérations suivantes :  
  
- insérer une demande d'autorisation pour toutes les autorisations que votre code doit posséder et gérer à l'avance la défaillance de durée de chargement qui se produit lorsque les autorisations ne sont pas accordées ;  
  
- ne pas utiliser de demande d'autorisation pour obtenir les autorisations dont votre code peut avoir besoin, mais être préparé à gérer les exceptions de sécurité lorsque les autorisations ne sont pas accordées.  
  
    > [!NOTE]
    >  La sécurité est un domaine complexe et vous pouvez effectuer votre choix parmi de nombreuses options. Pour plus d’informations, consultez [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md).  
  
 Au moment du chargement, la preuve de l'assembly est utilisée comme entrée vers la stratégie de sécurité. La stratégie de sécurité est établie par l'entreprise et l'administrateur de l'ordinateur, ainsi que par les paramètres de stratégie de l'utilisateur, et détermine le jeu d'autorisations qui est accordé à l'ensemble du code managé lors de son exécution. La stratégie de sécurité peut être établie pour l'éditeur de l'assembly (s'il possède une signature générée par un outil de signature), pour le site Web et la zone (selon les termes d'Internet Explorer) à partir desquels l'assembly a été téléchargé ou pour le nom fort de l'assembly. Par exemple, l'administrateur d'un ordinateur peut établir une stratégie de sécurité qui autorise l'ensemble d'un code téléchargé à partir d'un site Web et signé par un éditeur de logiciel donné d'accéder à une base de données sur un ordinateur, mais qui n'accorde pas d'accès en écriture sur le disque de l'ordinateur.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Assemblys avec nom fort et outils de signature  

 > [!WARNING]
 > Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.

 Vous pouvez signer un assembly de deux manières différentes, mais qui sont complémentaires : avec un nom fort ou à l’aide de [SignTool.exe (outil de signature)](../../../docs/framework/tools/signtool-exe.md). La signature d’un assembly avec un nom fort ajoute un chiffrement à clé publique au fichier contenant le manifeste d’assembly. La signature avec un nom fort permet de vérifier l'unicité du nom, empêche l'usurpation de noms et fournit aux appelants une certaine identité lorsqu'une référence est résolue.  
  
 Aucun niveau de confiance n’est associé à un nom fort, d’où l’importance accordée à l’outil de signature [SignTool.exe](../../../docs/framework/tools/signtool-exe.md). Les deux outils de signature exigent d'un éditeur qu'il prouve son identité à une tierce autorité et obtienne un certificat. Ce certificat est ensuite incorporé à votre fichier et peut être utilisé par un administrateur pour décider d'approuver ou non l'authenticité du code.  
  
 Vous pouvez attribuer à un assembly un nom fort et une signature numérique créés à l’aide de [SignTool.exe (outil de signature) ](../../../docs/framework/tools/signtool-exe.md), ou utiliser l’un ou l’autre indépendamment. Les deux outils de signature ne peuvent signer qu'un fichier à la fois ; pour un assembly multifichier, vous signez le fichier qui contient le manifeste d'assembly. Un nom fort est stocké dans un fichier qui contient le manifeste d’assembly, tandis qu’une signature créée à l’aide de l’outil de signature [SignTool.exe](../../../docs/framework/tools/signtool-exe.md) est stockée dans un emplacement réservé à cet effet, dans un fichier exécutable portable qui contient le manifeste d’assembly. La signature d’un assembly à l’aide de [l’outil de signature SignTool.exe](../../../docs/framework/tools/signtool-exe.md) peut être utilisée (avec ou sans nom fort) lorsque vous possédez déjà une hiérarchie de confiance qui s’appuie sur les signatures générées par cet [outil de signature SignTool.exe](../../../docs/framework/tools/signtool-exe.md), ou lorsque votre stratégie n’utilise que la partie propre à la clé et ne contrôle pas de chaîne de confiance.  
  
> [!NOTE]
>  Lorsque vous utilisez à la fois un nom fort et une signature générée par un outil avec un assembly, le nom fort doit être assigné en premier.  
  
 Le Common Language Runtime effectue également une vérification du hachage ; le manifeste d'assembly contient la liste de tous les fichiers qui composent l'assembly, y compris un hachage de chaque fichier tel qu'il existait lors de la génération du manifeste. À mesure que chaque fichier est chargé, son contenu est haché et comparé à la valeur de hachage stockée dans le manifeste. Si les deux hachages ne correspondent pas, l'assembly échoue.  
  
 Comme l’affectation de nom fort et la signature à l’aide de l’[outil de signature SignTool.exe](../../../docs/framework/tools/signtool-exe.md) garantissent l’intégrité, vous pouvez baser la stratégie de sécurité d’accès du code sur ces deux formes de preuve d’assembly. L’affectation de nom fort et la signature à l’aide de l’[outil de signature SignTool.exe](../../../docs/framework/tools/signtool-exe.md) garantissent l’intégrité par les signatures numériques et les certificats. Toutes les technologies mentionnées (vérification du hachage, affectation de nom fort et signature à l’aide de l’[outil de signature SignTool.exe](../../../docs/framework/tools/signtool-exe.md)) fonctionnent ensemble pour que l’assembly ne soit pas altéré d’une manière ou d’une autre.  
  
## <a name="see-also"></a>Voir aussi

- [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [SignTool.exe (outil de signature)](../../../docs/framework/tools/signtool-exe.md)
