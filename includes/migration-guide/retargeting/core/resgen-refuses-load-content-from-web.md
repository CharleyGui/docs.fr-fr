---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614518"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>Resgen refuse de charger le contenu à partir du Web

#### <a name="details"></a>Détails

les fichiers. resx peuvent contenir une entrée au format binaire. Si vous tentez d’utiliser Resgen pour charger un fichier qui a été téléchargé à partir d’un emplacement non approuvé, il ne parviendra pas à charger l’entrée par défaut.

#### <a name="suggestion"></a>Suggestion

Les utilisateurs Resgen qui requièrent le chargement d’une entrée au format binaire à partir d’emplacements non approuvés peuvent supprimer la marque du Web du fichier d’entrée ou appliquer la particularité de l’annulation. Ajoutez le paramètre de Registre suivant pour appliquer la particularité de l’annulation de l’ordinateur : [HKEY_LOCAL_MACHINE \Software\Microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |
