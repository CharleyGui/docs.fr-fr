---
title: Manifeste d'assembly
description: Un manifeste d’assembly .NET spécifie ses exigences en matière de version, l’identité de sécurité et la portée de l’assembly et les informations pour résoudre les références.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
ms.openlocfilehash: 4f4d09f559ac66e1f3bc38af0781f7e01e7461d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380168"
---
# <a name="assembly-manifest"></a>Manifeste d'assembly
Chaque assembly, qu'il soit statique ou dynamique, comporte une collection de données qui décrit comment les éléments de l'assembly sont reliés les uns aux autres. Le manifeste d'assembly contient les métadonnées de l'assembly. Un manifeste d'assembly comprend toutes les métadonnées nécessaires pour spécifier la version requise et l'identité de sécurité de l'assembly, ainsi que toutes les métadonnées nécessaires pour définir la portée de l'assembly et résoudre les références aux ressources et aux classes. Le manifeste d’assembly peut être stocké dans un fichier PE ( *. exe* ou *. dll*) avec le code MSIL (Microsoft Intermediate Language) ou dans un fichier PE autonome qui contient uniquement des informations de manifeste d’assembly.  
  
 L'illustration ci-dessous indique les différents modes de stockage du manifeste.  
  
 ![Diagramme qui montre le manifeste dans un assembly à fichier unique et la configuration de l’assembly multifichier.](./media/manifest/assembly-types-diagram.gif)  
  
 Pour un assembly avec un fichier associé, le manifeste est incorporé au fichier PE pour former un assembly monofichier. Vous pouvez créer un assembly multifichier avec un fichier manifeste autonome ou avec le manifeste incorporé à l'un des fichiers PE de l'assembly.  
  
 Le manifeste de chaque assembly exécute les fonctions suivantes :  
  
- Il énumère les fichiers qui composent l'assembly.  
  
- Il détermine le mode de mappage des références aux types et aux ressources de l'assembly aux fichiers qui contiennent leurs déclarations et leurs implémentations.  
  
- Il énumère les autres assemblys dont l'assembly dépend.  
  
- Il fournit un niveau d'adressage indirect entre les consommateurs de l'assembly et les détails d'implémentation de l'assembly.  
  
- Il rend l'assembly autodescriptif.  
  
## <a name="assembly-manifest-contents"></a>Contenu du manifeste de l’assembly  
 Le tableau suivant indique les informations qui figurent dans le manifeste d'assembly. Les quatre premiers éléments suivants : le nom de l’assembly, le numéro de version, la culture et les informations de nom fort constituent l’identité de l’assembly.  
  
|Information|Description|  
|-----------------|-----------------|  
|Nom de l'assembly|Chaîne de texte spécifiant le nom de l'assembly.|  
|Numéro de version|Numéro de version principale et secondaire et numéro de révision et de build. Le Common Language Runtime utilise ces numéros pour appliquer la stratégie de version.|  
|Culture|Informations sur la culture ou le langage que l'assembly prend en charge. Ces informations ne doivent être utilisées que pour désigner un assembly en tant qu'assembly satellite contenant des informations spécifiques à la culture ou au langage. Un assembly possédant des informations sur la culture est automatiquement considéré comme étant un assembly satellite.|  
|Informations sur le nom fort|Clé publique de l'éditeur si un nom fort a été attribué à l'assembly.|  
|Liste de tous les fichiers figurant dans l'assembly|Hachage de chaque fichier figurant dans l'assembly et nom de fichier. Notez que tous les fichiers qui composent l'assembly doivent figurer dans le même répertoire que le fichier qui comporte le manifeste d'assembly.|  
|Informations sur les références de type|Informations utilisées par le runtime pour mapper une référence de type au fichier qui contient sa déclaration et son implémentation. Elles sont utilisées pour les types qui sont exportés à partir de l'assembly.|  
|Informations sur les assemblys référencés|Liste des autres assemblys statiquement référencés par l'assembly. Chaque référence inclut le nom de l'assembly dépendant, les métadonnées de l'assembly (version, culture, système d'exploitation...) et la clé publique, si l'assembly possède un nom fort.|  
  
 Vous pouvez ajouter ou modifier certaines informations dans le manifeste d'assembly en utilisant des attributs d'assembly dans votre code. Vous pouvez modifier les informations sur la version et les attributs d'informations, y compris la Marque, le Copyright, le Produit, la Société et la Version d'informations. Pour obtenir la liste complète des attributs d’assembly, consultez [définir des attributs d’assembly](set-attributes.md).  
  
## <a name="see-also"></a>Voir aussi

- [Contenu d’assembly](contents.md)
- [Contrôle de version des assemblys](versioning.md)
- [Créer des assemblys satellites](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Assemblys avec nom fort](strong-named.md)
