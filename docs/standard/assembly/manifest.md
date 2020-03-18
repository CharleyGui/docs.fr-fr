---
title: Manifeste d'assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
ms.openlocfilehash: f1913f8c41ba4a7b54f7abcdfb97400503da8ac5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73107153"
---
# <a name="assembly-manifest"></a>Manifeste d'assembly
Chaque assembly, qu'il soit statique ou dynamique, comporte une collection de données qui décrit comment les éléments de l'assembly sont reliés les uns aux autres. Le manifeste d'assembly contient les métadonnées de l'assembly. Un manifeste d'assembly comprend toutes les métadonnées nécessaires pour spécifier la version requise et l'identité de sécurité de l'assembly, ainsi que toutes les métadonnées nécessaires pour définir la portée de l'assembly et résoudre les références aux ressources et aux classes. Le manifeste d’assemblage peut être stocké dans un fichier PE (un *.exe* ou *.dll*) avec le code microsoft langue intermédiaire (MSIL) ou dans un fichier PE autonome qui ne contient que des informations manifestes d’assemblage.  
  
 L'illustration ci-dessous indique les différents modes de stockage du manifeste.  
  
 ![Diagramme qui montre le manifeste dans un assembly à fichier unique et la configuration de l’assembly multifichier.](./media/manifest/assembly-types-diagram.gif)  
  
 Pour un assembly avec un fichier associé, le manifeste est incorporé au fichier PE pour former un assembly monofichier. Vous pouvez créer un assembly multifichier avec un fichier manifeste autonome ou avec le manifeste incorporé à l'un des fichiers PE de l'assembly.  
  
 Le manifeste de chaque assembly exécute les fonctions suivantes :  
  
- Il énumère les fichiers qui composent l'assembly.  
  
- Il détermine le mode de mappage des références aux types et aux ressources de l'assembly aux fichiers qui contiennent leurs déclarations et leurs implémentations.  
  
- Il énumère les autres assemblys dont l'assembly dépend.  
  
- Il fournit un niveau d'adressage indirect entre les consommateurs de l'assembly et les détails d'implémentation de l'assembly.  
  
- Il rend l'assembly autodescriptif.  
  
## <a name="assembly-manifest-contents"></a>Contenu manifeste de l’assemblage  
 Le tableau suivant indique les informations qui figurent dans le manifeste d'assembly. Les quatre premiers éléments : nom de l’assemblage, numéro de version, culture et informations sur le nom fort composent l’identité de l’assemblée.  
  
|Information|Description|  
|-----------------|-----------------|  
|Nom de l'assembly|Chaîne de texte spécifiant le nom de l'assembly.|  
|Numéro de version|Numéro de version principale et secondaire et numéro de révision et de build. Le Common Language Runtime utilise ces numéros pour appliquer la stratégie de version.|  
|Culture|Informations sur la culture ou le langage que l'assembly prend en charge. Ces informations ne doivent être utilisées que pour désigner un assembly en tant qu'assembly satellite contenant des informations spécifiques à la culture ou au langage. Un assembly possédant des informations sur la culture est automatiquement considéré comme étant un assembly satellite.|  
|Informations sur le nom fort|Clé publique de l'éditeur si un nom fort a été attribué à l'assembly.|  
|Liste de tous les fichiers figurant dans l'assembly|Hachage de chaque fichier figurant dans l'assembly et nom de fichier. Notez que tous les fichiers qui composent l'assembly doivent figurer dans le même répertoire que le fichier qui comporte le manifeste d'assembly.|  
|Informations sur les références de type|Informations utilisées par le runtime pour mapper une référence de type au fichier qui contient sa déclaration et son implémentation. Elles sont utilisées pour les types qui sont exportés à partir de l'assembly.|  
|Informations sur les assemblys référencés|Liste des autres assemblys statiquement référencés par l'assembly. Chaque référence inclut le nom de l'assembly dépendant, les métadonnées de l'assembly (version, culture, système d'exploitation...) et la clé publique, si l'assembly possède un nom fort.|  
  
 Vous pouvez ajouter ou modifier certaines informations dans le manifeste d'assembly en utilisant des attributs d'assembly dans votre code. Vous pouvez modifier les informations sur la version et les attributs d'informations, y compris la Marque, le Copyright, le Produit, la Société et la Version d'informations. Pour une liste complète des attributs d’assemblage, voir [les attributs d’assemblage d’ensemble.](set-attributes.md)  
  
## <a name="see-also"></a>Voir aussi

- [Contenu d’assembly](contents.md)
- [Contrôle de version des assemblys](versioning.md)
- [Créer des assemblys satellites](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Assemblées de bien-être](strong-named.md)
