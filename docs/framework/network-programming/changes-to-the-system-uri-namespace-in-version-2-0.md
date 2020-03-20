---
title: Modifications apportées à l’espace de noms System.Uri dans la version 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642761"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Modifications apportées à l’espace de noms System.Uri dans la version 2.0

Plusieurs modifications ont été apportées à la classe <xref:System.Uri?displayProperty=nameWithType>. Ces modifications éliminent un comportement incorrect, améliorent la convivialité et renforcent la sécurité.

## <a name="obsolete-and-deprecated-members"></a>Membres obsolètes et déconseillés

 Constructeurs :

- Tous les constructeurs qui ont un paramètre `dontEscape`.

 Méthodes :

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a>Modifications

- Pour les schémas d’URI qui sont connus comme n’ayant aucune partie de requête (file, ftp, etc.), le caractère « ? » est toujours placé dans une séquence d’échappement et n’est pas considéré comme le début d’une partie <xref:System.Uri.Query%2A>.

- Pour les URI de fichiers implicites (au format `c:\directory\file@name.txt`), le caractère de fragment (« # ») est toujours placé dans une séquence d’échappement, sauf si l’absence totale de séquence d’échappement est demandée ou si <xref:System.Uri.LocalPath%2A> a la valeur `true`.

- La prise en charge des noms d’hôtes UNC a été supprimée ; la spécification IDN pour la représentation des noms d’hôtes internationaux a été adoptée.

- <xref:System.Uri.LocalPath%2A> retourne toujours une chaîne sans séquence d’échappement.

- <xref:System.Uri.ToString%2A> ne supprime pas la séquence d’échappement d’un caractère « % », « ? » ou « # » placé dans une séquence d’échappement.

- <xref:System.Uri.Equals%2A> inclut désormais la partie <xref:System.Uri.Query%2A> dans la vérification de l’égalité.

- Les opérateurs « = » et « != » sont substitués et liés à la méthode <xref:System.Uri.Equals%2A>.

- <xref:System.Uri.IsLoopback%2A> produit maintenant des résultats cohérents.

- L’URI « `file:///path` » n’est plus traduite en `file://path`.

- « # » est maintenant reconnu comme un terminateur de nom d’hôte. En d’autres termes, `http://contoso.com#fragment` est désormais converti en `http://contoso.com/#fragment`.

- Un bogue présent lors de la combinaison d’un URI de base avec un fragment a été résolu.

- Un bogue dans <xref:System.Uri.HostNameType%2A> a été résolu.

- Un bogue dans l’analyse NNTP a été résolu.

- Un URI au format HTTP:contoso.com lève désormais une exception d’analyse.

- Le Framework gère correctement userinfo dans un URI.

- La compression de chemin d’URI a été résolue afin qu’un URI rompu ne puisse pas parcourir le système de fichiers au-dessus de la racine.

## <a name="see-also"></a>Voir aussi

- <xref:System.Uri?displayProperty=nameWithType>
