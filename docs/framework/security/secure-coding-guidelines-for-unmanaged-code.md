---
title: Instructions de codage sécurisé pour le code non managé
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec97861a9d748767199da3e1fb7f53361c3a48ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966121"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Instructions de codage sécurisé pour le code non managé
Du code de bibliothèque doit appeler dans du code non managé (par exemple, des API de code natif comme Win32). Comme cela signifie sortir du périmètre de sécurité pour le code managé, la prudence est de règle. S’il ne dépend pas de la sécurité, votre code, ainsi que tout code qui l’appelle, doit disposer de l’autorisation de code non managé (<xref:System.Security.Permissions.SecurityPermission> avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> spécifié).  
  
 Cependant, il est souvent préférable que votre appelant ne possède pas des autorisations aussi puissantes. Dans ces cas-là, votre code fiable peut servir d'intermédiaire, de la même manière que le wrapper managé ou le code de bibliothèque décrit dans [Sécurisation du code wrapper](../../../docs/framework/misc/securing-wrapper-code.md). Si les fonctionnalités de code non managé sous-jacentes sont totalement sécurisées, elles risquent d'être exposées directement ; si cela n'est pas le cas, une vérification d'autorisation appropriée (demande) est nécessaire dans un premier temps.  
  
 Quand votre code appelle dans du code non managé mais que vous ne souhaitez pas que vos appelants soient obligés d'avoir l'autorisation d'accéder à du code non managé, vous devez déclarer ce droit. Une assertion bloque le parcours de la pile à votre frame. Vous devez faire attention à ne pas créer de faille de sécurité pendant ce processus. Habituellement, cela signifie que vous devez exiger une autorisation appropriée de vos appelants, puis vous servir du code non managé pour effectuer uniquement ce que cette autorisation permet et rien de plus. Dans certains cas (par exemple, une fonction récupérant l'heure du jour), du code non managé peut être directement exposé aux appelants sans vérification de la sécurité. Dans tous les cas, tout code qui déclare doit être responsable de la sécurité.  
  
 Comme tout code managé qui fournit un chemin de code dans le code natif est une cible potentielle pour du code nuisible, déterminer le type de code non managé qui peut s'utiliser sans risque et la manière de l'utiliser nécessite beaucoup de précautions. Généralement, il ne faut jamais exposer du code non managé directement à des appelants d'un niveau de confiance partiel. Deux considérations principales gouvernent l'évaluation de la sécurité de l'utilisation de code non managé dans des bibliothèques pouvant être appelées par du code d'un niveau de confiance partiel :  
  
- **Fonctionnalité**. Est-ce que l'API non managée fournit des fonctionnalités qui ne permettent pas aux appelants d'effectuer des opérations potentiellement risquées ? Comme la sécurité d'accès du code utilise des autorisations pour faire appliquer l'accès aux ressources, vous devez envisager si l'API utilise des fichiers, une interface utilisateur ou des technologies de threads ou si elle expose des informations protégées. Si tel est le cas, le code managé qui l'englobe doit exiger les autorisations nécessaires avant d'autoriser son entrée. De plus, même s'il ne fait pas l'objet d'une protection par autorisation, l'accès à la mémoire doit se limiter à la sécurité stricte des types.  
  
- **Vérification des paramètres**. Une attaque courante passe des paramètres inattendus à des méthodes API de code non managé exposées dans le but de les faire fonctionner hors spécification. Le dépassement de mémoire tampon utilisant des index non valides ou des valeurs offset constitue un exemple courant de ce type d'attaque, comme tous les paramètres qui risquent d'exploiter un bogue dans le code sous-jacent. Ainsi, même si l'API du code non managé est sécurisée du point de vue fonctionnel (après des demandes nécessaires) pour des appelants d'un niveau de confiance partiel, le code managé doit également vérifier la validité des paramètres de manière exhaustive pour garantir qu'aucun appel involontaire n'est possible par du code nuisible utilisant la couche wrapper du code managé.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Utilisation de SuppressUnmanagedCodeSecurityAttribute  
 Il existe un aspect performance lié à la déclaration, puis à l'appel de code non managé. Pour chaque appel de ce type, le système de sécurité exige automatiquement l'autorisation du code non managé, ce qui entraîne à chaque fois un parcours de pile. Si vous déclarez et appelez immédiatement du code non managé, le parcours de pile peut s'avérer inutile : il comporte votre déclaration et votre appel de code non managé.  
  
 Un attribut personnalisé nommé <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> peut être appliqué à des points d’entrée du code non managé pour désactiver la vérification de sécurité normale qui exige <xref:System.Security.Permissions.SecurityPermission> avec l’autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> spécifiée. Vous devez effectuer ces opérations en observant systématiquement la plus grande précaution, car cette action crée une porte ouverte dans du code non managé sans vérification de sécurité au moment de l'exécution. Notez que même si **SuppressUnmanagedCodeSecurityAttribute** est appliqué, une vérification de sécurité unique a lieu au moment de la compilation juste-à-temps (JIT, Just-In-Time) pour garantir que l'appelant immédiat possède l'autorisation d'appeler du code non managé.  
  
 Si vous utilisez **SuppressUnmanagedCodeSecurityAttribute**, vérifiez les points suivants :  
  
- Faites en sorte que le point d'entrée du code non managé soit interne ou, si cela n'est pas possible, qu'il soit inaccessible hors de votre code.  
  
- Tout appel dans du code non managé représente une faille de sécurité potentielle. Veillez à ce que votre code ne soit pas une porte ouverte à un appel indirect par du code nuisible dans du code non managé évitant ainsi une vérification de sécurité. Exigez des autorisations, si cela est approprié.  
  
- Utilisez une convention d'affectation de noms pour identifier de manière explicite les cas où vous créez un chemin à risque dans du code non managé, comme indiqué dans la section ci-dessous.  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Convention d'affectation de noms pour les méthodes de code non managé  
 Une convention utile et fortement recommandée a été créée pour nommer des méthodes de code non managé. Toutes les méthodes de code non managé sont divisées en trois catégories : **safe**, **native**et **unsafe**. Ces mots clés peuvent être utilisés comme noms de classe dans lesquels les différents types de points d'entrée du code non managé sont définis. Dans le code source, ces mots clés doivent être ajoutés au nom de la classe, comme pour `Safe.GetTimeOfDay`, `Native.Xyz`ou `Unsafe.DangerousAPI`, par exemple. Chacun de ces mots clés fournit les informations de sécurité nécessaires aux développeurs utilisant cette classe, comme le montre le tableau suivant :  
  
|Mot clé|Considérations relatives à la sécurité|  
|-------------|-----------------------------|  
|**safe**|Ne présente aucun danger pour un appel par n'importe quel code, même du code nuisible. Peut s'utiliser comme n'importe quel autre code managé. Par exemple, une fonction qui récupère l'heure du jour est en général sécurisée.|  
|**native**|Indépendant de la sécurité ; c'est-à-dire du code non managé qui nécessite l'autorisation du code non managé pour appeler. La sécurité est vérifiée, ce qui bloque un appelant non autorisé.|  
|**unsafe**|Point d'entrée dans du code non managé potentiellement dangereux et sans sécurité. Les développeurs doivent faire preuve d'une grande prudence quand ils utilisent ce code non managé en veillant à ce que les autres protections soient en place afin d'éviter une faille en matière de sécurité. Les développeurs doivent se montrer responsables, car ce mot clé substitue le système de sécurité.|  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
