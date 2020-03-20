---
title: Storeadm.exe (outil Isolated Storage)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715713"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (outil Isolated Storage)
L'outil Isolated Storage (Stockage isolé) répertorie ou supprime tous les magasins existants de l'utilisateur en cours.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Option|Description|  
|------------|-----------------|  
|**/h**[**elp**]|Affiche la syntaxe et les options de commande de l'outil.|  
|**/liste**|Affiche tous les magasins existants de l'utilisateur en cours. Sont inclus les magasins de toutes les applications ou de tous les assemblys exécutés par cet utilisateur.|  
|**/machine**|Sélectionne le magasin de l'ordinateur. Utilisez cette option avec l’option **/list** ou **/remove** pour spécifier que l’action doit s’appliquer au magasin de l’ordinateur.<br /><br /> Nouveau dans le .NET Framework 2.0|  
|**/calme**|Spécifie le mode silencieux ; supprime la sortie d'informations pour n'afficher que les messages d'erreur.|  
|**/supprimer**|Supprime définitivement tous les magasins existants de l'utilisateur en cours.|  
|**/roaming**|Sélectionne le magasin itinérant. Utilisez cette option avec l’option **/list** ou **/remove** pour spécifier que cette action doit s’appliquer au magasin itinérant.|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Notes   
 Lorsque vous exécutez Storeadm.exe à partir de la ligne de commande sans spécifier d'options, la syntaxe et les options de l'outil s'affichent.  
  
 Les options **/list** et **/remove** sont généralement utilisées l’une après l’autre ; si deux options ou plus sont spécifiées, elles sont alors exécutées dans leur ordre d’apparition sur la ligne de commande.  
  
 Les applications peuvent enregistrer soit dans l'un des deux magasins d'un utilisateur, soit dans le magasin de l'ordinateur :  
  
- Le magasin local est situé à un emplacement assuré de ne pas être itinérant (sur Windows 2000 et ultérieur), même si le profil d’utilisateur itinérant est activé pour cet utilisateur.  
  
- Le magasin itinérant est situé à un emplacement pouvant être itinérant, mais uniquement quand l’itinérance est activée pour l’utilisateur par le biais de l’administration de Windows NT.  
  
- Le magasin de l'ordinateur est commun à tous les utilisateurs sur un ordinateur et est stocké sous un répertoire commun de cet ordinateur.  
  
    > [!NOTE]
    > Le magasin d'ordinateur est une nouveauté du .NET Framework version 2.0.  
  
 Que l'itinérance soit ou non réellement activée pour l'utilisateur n'affecte pas l'administration de Storeadm.exe. L'exécution de l'outil sans option applique toutes les actions au magasin local. L’exécution de l’outil avec l’option **/roaming** affecte toutes les actions au magasin qui est capable d’effectuer l’itinérance. L’exécution de l’outil avec l’option **/machine** affecte toutes les actions au magasin de l’ordinateur.  
  
## <a name="see-also"></a>Voir aussi

- [Outils](index.md)
- [Stockage isolé](../../standard/io/isolated-storage.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
