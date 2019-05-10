---
title: Sécurité et entrées d'utilisateur
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce6dd2fcf913c16e4da68dec35ea3ccd8e90a948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665781"
---
# <a name="security-and-user-input"></a>Sécurité et entrées d'utilisateur
Les données utilisateurs, quel que soit le type d’entrée (données d’une demande web ou URL, entrée de commandes d’une application Windows Forms, etc.), peuvent affecter négativement le code, dans la mesure où ces données sont souvent utilisées directement en tant que paramètres pour appeler un autre code. Cette situation, similaire à l’appel de votre code par du code malveillant à l’aide de paramètres étranges, nécessite les mêmes précautions. En réalité, une entrée utilisateur est plus difficile à sécuriser, car il n’existe aucune frame de pile permettant de détecter la présence de données potentiellement non fiables.  
  
 Il s’agit des bogues de sécurité les plus subtils et les plus difficiles à identifier car, bien qu’ils peuvent apparaître dans du code en apparence non lié à la sécurité, ils constituent une passerelle permettant de transférer des données incorrectes vers d’autres codes. Pour rechercher ces bogues, suivez tout type de données d’entrée, imaginez la fourchette de valeurs possibles, et déterminez si le code traitant ces données peut traiter l’ensemble des cas. Pour corriger ces bogues, procédez à une vérification de plage, puis rejetez toute entrée ne pouvant pas être traitée par le code.  
  
 Voici quelques considérations importantes associées aux données utilisateurs :  
  
- Toutes les données utilisateur d’une réponse de serveur s’exécutent dans le contexte du site du serveur sur le client. Si votre serveur web utilise des données utilisateur qu’il insère dans la page web renvoyée, il peut, par exemple, inclure une balise **\<script>** et l’exécuter comme si l’opération était effectuée par le serveur.  
  
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

- [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)
