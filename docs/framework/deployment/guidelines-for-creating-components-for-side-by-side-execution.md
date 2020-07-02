---
title: Indications pour la création de composants pour l'exécution côte à côte
description: Passez en revue les instructions relatives à la création de composants pour l’exécution côte à côte. Par exemple, liez l’identité de type à une certaine version de fichier ou utilisez un stockage prenant en compte la version.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: f0d25984f2444d29d9fc0edb3add23b6adc04c62
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622638"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Indications pour la création de composants pour l'exécution côte à côte
Suivez ces recommandations générales pour créer des applications managées ou des composants conçus pour l'exécution côte à côte :  
  
- Associer l'identité de type à une version particulière d'un fichier.  
  
     Le CLR (Common Language Runtime) associe l'identité de type à une version de fichier particulière à l'aide d'assemblys avec un nom fort. Pour créer une application ou un composant pour l'exécution côte à côte, vous devez donner à tous les assemblys un nom fort. Cela crée une identité de type précise et garantit que toute résolution de type est dirigée vers le fichier approprié. Un assembly avec nom fort contient des informations sur la version, la culture et l'éditeur que le runtime utilise pour localiser le fichier approprié afin de répondre à une demande de liaison.  
  
- Utilisez un stockage prenant en compte la version.  
  
     Le runtime utilise le Global Assembly Cache pour fournir un stockage prenant en compte la version. Le Global Assembly Cache est une structure de répertoire prenant en compte la version installée sur chaque ordinateur qui utilise le .NET Framework. Les assemblys installés dans le Global Assembly Cache ne sont pas remplacés quand une nouvelle version de cet assembly est installée.  
  
- Créez une application ou un composant qui s'exécute de manière isolée.  
  
     Une application ou un composant qui s'exécute de manière isolée doit gérer les ressources de sorte à éviter des conflits quand deux instances de l'application ou du composant sont exécutées simultanément. L'application ou le composant doit également utiliser une structure de fichiers propre à la version.  
  
## <a name="application-and-component-isolation"></a>Isolement d'application et de composant  
 L'isolement est l'un des moyens permettant de correctement concevoir une application ou un composant pour l'exécution côte à côte. L'application ou le composant doit gérer toutes les ressources, en particulier l'E/S des fichiers, de manière isolée. Suivez ces instructions pour vous assurer que votre application ou composant s'exécute de manière isolée :  
  
- Écrivez dans le Registre en tenant compte de la version. Stockez des valeurs dans des ruches ou des clés qui indiquent la version, et ne partagez pas des informations ou un état entre les versions d'un composant. Cela permet d'éviter que deux applications ou composants qui s'exécutent en même temps remplacent les informations.  
  
- Faites en sorte que les objets de noyau nommés soient propres à la version pour éviter une condition de concurrence. Par exemple, une condition de concurrence se produit quand deux sémaphores de deux versions de la même application s'attendent mutuellement.  
  
- Choisissez des noms de fichiers et répertoires qui prennent en compte la version. Cela signifie que les structures de fichiers doivent reposer sur les informations de version.  
  
- Créez des comptes et groupes d'utilisateur en tenant compte de la version. Les comptes et groupes d'utilisateurs créés par une application doivent être identifiés par la version. Ne partagez pas les comptes et groupes d'utilisateurs entre les versions d'une application.  
  
## <a name="installing-and-uninstalling-versions"></a>Installation et désinstallation de versions  
 Quand vous concevez une application pour l'exécution côte à côte, suivez ces indications concernant l'installation et la désinstallation des versions :  
  
- Ne supprimez pas les informations du Registre qui peuvent être requises par d'autres applications s'exécutant sous une version différente du .NET Framework.  
  
- Ne remplacez pas les informations du Registre qui peuvent être requises par d'autres applications s'exécutant sous une version différente du .NET Framework.  
  
- N'annulez pas l'enregistrement de composants COM qui peuvent être requis par d'autres applications s'exécutant sous une version différente du .NET Framework.  
  
- Ne modifiez pas **InprocServer32** ou d’autres entrées de Registre pour un serveur COM qui a déjà été enregistré.  
  
- Ne supprimez pas des comptes ou groupes d'utilisateur qui peuvent être requis par d'autres applications s'exécutant sous une version différente du .NET Framework.  
  
- N'ajoutez pas d'entrée dans le Registre qui contient un chemin d'accès sans version.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Numéro de version de fichier et numéro de version d'assembly  
 La version de fichier est une ressource de version Win32 qui n'est pas utilisée par le runtime. En général, vous mettez à jour la version de fichier même pour une mise à jour sur place. Deux fichiers identiques peuvent avoir des informations de version de fichier différentes, et deux fichiers différents peuvent avoir des informations de version de fichier identiques.  
  
 La version d'assembly est utilisée par le runtime pour la liaison d'assembly. Deux assemblys identiques avec des numéros de version différents sont traités comme deux assemblys différents par le runtime.  
  
 L’[outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) vous permet de remplacer un assembly quand seul le numéro de version de fichier est plus récent. Le programme d'installation ne remplace généralement pas un assembly, sauf si le numéro de version d'assembly est supérieur.  
  
## <a name="see-also"></a>Voir aussi

- [Exécution côte à côte](side-by-side-execution.md)
- [Procédure : Activer et désactiver la redirection de liaison automatique](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
