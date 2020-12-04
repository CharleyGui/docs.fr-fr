---
title: Règles de portabilité et d’interopérabilité (analyse du code)
description: En savoir plus sur les règles de portabilité et d’interopérabilité des règles d’analyse du code
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586965"
---
# <a name="portability-and-interoperability-rules"></a>Règles de portabilité et d’interopérabilité

Les règles de portabilité prennent en charge la portabilité sur différentes plateformes. Les règles d’interopérabilité prennent en charge l’interaction avec les clients COM.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [Ca1401 : les P/Invoke ne doivent pas être visibles](ca1401.md) | Une méthode publique ou protégée dans un type public a l’attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare dans Visual Basic). De telles méthodes ne doivent pas être exposées. |
| [CA1416 : Valider la compatibilité de la plateforme](ca1416.md) | L’utilisation d’API dépendant de la plateforme sur un composant rend le code ne plus fonctionner sur toutes les plateformes. |
| [Ca1417 : ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour les P/Invoke](ca1417.md) | Les paramètres de chaîne passés par valeur avec le `OutAttribute` peuvent déstabiliser le runtime si la chaîne est une chaîne internée. |
