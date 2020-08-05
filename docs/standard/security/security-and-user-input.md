---
title: Sécurité et entrées d'utilisateur
description: Votre code peut passer des données entrées par l’utilisateur en tant que paramètres à un autre code, ce qui peut affecter la sécurité. Vous pouvez effectuer une vérification de plage pour rejeter les entrées problématiques.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: e46bf8e653567637b4e6236849981fdb32df447c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555940"
---
# <a name="security-and-user-input"></a>Sécurité et entrées d'utilisateur

Les données utilisateurs, quel que soit le type d’entrée (données d’une demande web ou URL, entrée de commandes d’une application Windows Forms, etc.), peuvent affecter négativement le code, dans la mesure où ces données sont souvent utilisées directement en tant que paramètres pour appeler un autre code. Cette situation, similaire à l’appel de votre code par du code malveillant à l’aide de paramètres étranges, nécessite les mêmes précautions. En réalité, une entrée utilisateur est plus difficile à sécuriser, car il n’existe aucune frame de pile permettant de détecter la présence de données potentiellement non fiables.

Il s’agit des bogues de sécurité les plus subtils et les plus difficiles à identifier car, bien qu’ils peuvent apparaître dans du code en apparence non lié à la sécurité, ils constituent une passerelle permettant de transférer des données incorrectes vers d’autres codes. Pour rechercher ces bogues, suivez tout type de données d’entrée, imaginez la fourchette de valeurs possibles, et déterminez si le code traitant ces données peut traiter l’ensemble des cas. Pour corriger ces bogues, procédez à une vérification de plage, puis rejetez toute entrée ne pouvant pas être traitée par le code.

Voici quelques considérations importantes associées aux données utilisateurs :

- Toutes les données utilisateur d’une réponse de serveur s’exécutent dans le contexte du site du serveur sur le client. Si votre serveur Web utilise des données utilisateur et les insère dans la page Web renvoyée, il peut, par exemple, inclure une **\<script>** balise et l’exécuter comme si elle était à partir du serveur.

- N’oubliez pas que le client peut demander toute URL.

- Tenez compte des chemins d’accès délicats ou non valides :

  - ..\ , des chemins d’accès extrêmement longs.

  - Utilisation de caractères génériques (*).

  - Expansion de jeton (%token%).

  - Formes étranges de chemins d’accès présentant une signification spécifique.

  - Autres noms de flux de système de fichiers, comme `filename::$DATA`.

  - Versions courtes de noms de fichiers, comme `longfi~1` pour `longfilename`.

- N’oubliez pas que la commande Eval(userdata) peut effectuer tout type d’action.

- Méfiez-vous de toute liaison tardive vers un nom comprenant des données utilisateur.

- Si vous traitez des données web, tenez compte des différents types d’échappements autorisés, notamment des suivants :

  - Échappements haxadécimaux (%nn).

  - Échappements Unicode (%nnn).

  - Échappements UTF-8 longs (%nn%nn).

  - Doubles échappements (%nn devient %mmnn, où %mm est l’échappement de %).

- Méfiez-vous des noms utilisateur pouvant présenter plusieurs formats canoniques. Par exemple, bien souvent, vous pouvez utiliser le format MONDOMAINE\\*nomutilisateur* ou le format *nomutilisateur*@mydomain.example.com.

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](secure-coding-guidelines.md)
- [Sécurité ASP.NET Core](/aspnet/core/security/)
