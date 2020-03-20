---
title: Configuration requise pour le fournisseur de données .NET Framework pour Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: dab3378d3022c01c674640201a67f3bdbb4f571f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174249"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Configuration requise pour le fournisseur de données .NET Framework pour Oracle

Le fournisseur de données .NET Framework pour Oracle requiert l'installation de Microsoft Data Access Components (MDAC) version 2.6 ou ultérieure. MDAC 2.8 SP1 est recommandé.  
  
 Oracle 8i Client mise en production 3 (8.1.7) ou ultérieure doit également être installé.  
  
 Les logiciels clients Oracle antérieurs à la version Oracle 9i ne peuvent pas accéder aux bases de données UTF16 parce que UTF16 est une nouvelle fonctionnalité d’Oracle 9i. Pour utiliser cette fonctionnalité, vous devez mettre à niveau votre logiciel client vers Oracle 9i ou une version ultérieure.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Utilisation du fournisseur de données pour Oracle et données Unicode  

Ce qui suit est une liste des questions liées à Unicode que vous devriez prendre en considération lorsque vous travaillez avec le fournisseur de données cadre .NET pour les bibliothèques de clients Oracle et Oracle. Pour plus d'informations, voir la documentation Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Définition de la valeur Unicode dans un attribut de chaîne de connexion  

Lorsque vous travaillez avec Oracle, vous pouvez utiliser l'attribut de chaîne de connexion   
  
`Unicode=True`
  
pour initialiser les bibliothèques du client Oracle en mode UTF-16. Cela a pour effet que les bibliothèques du client Oracle acceptent UTF-16 (qui est très similaire à UCS-2) à la place des chaînes multioctet. Cela permet au fournisseur de données pour Oracle de pouvoir toujours travailler avec une page de code Oracle quelconque sans que cela nécessite un travail de conversion supplémentaire. Cette configuration ne fonctionne que si vous utilisez des clients Oracle 9i pour communiquer avec une base de données Oracle 9i à l'aide de l'ensemble de caractères de remplacement de AL16UTF16. Lorsqu’un client Oracle 9i communique avec un serveur Oracle 9i, des ressources supplémentaires sont nécessaires pour convertir les valeurs Unicode **CommandText** en l’ensemble de caractères multi-byte approprié que le serveur Oracle9i utilise. Cela peut être évité lorsque vous savez que vous disposez de la configuration sécurisée en ajoutant `Unicode=True` à votre chaîne de connexion.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Mélange de versions de client Oracle et de serveur Oracle  

Les clients d’Oracle 8i ne peuvent pas accéder aux données **NCHAR**, **NVARCHAR2**ou **NCLOB** dans les bases de données Oracle 9i lorsque l’ensemble de caractères nationaux du serveur est spécifié sous le nom d’AL16UTF16 (le paramètre par défaut pour Oracle 9i). Comme la prise en charge de l'ensemble de caractères UTF-16 n'a été introduite qu'avec Oracle 9i, les clients Oracle 8i ne peuvent pas le lire.  
  
### <a name="working-with-utf-8-data"></a>Utilisation de données UTF-8  

Pour définir l'ensemble de caractères de remplacement, définissez la clé de registre HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG sur UTF8. Pour plus d'informations, voir les notes d'installation Oracle sur votre plateforme. Le paramétrage par défaut est l'ensemble de caractères principal de la langue dans laquelle vous installez le logiciel client Oracle. Si vous ne définissez pas la langue de façon à ce qu'elle corresponde à l'ensemble de caractères de la langue nationale de la base de données à laquelle vous vous connectez, cela a pour effet que les liaisons de paramètres et de colonnes envoient ou reçoivent des données dans l'ensemble de caractères de votre base de données principale et non dans l'ensemble de caractères national.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob ne peut mettre à jour que des caractères complets.  

Pour des raisons <xref:System.Data.OracleClient.OracleLob> d’utilisabilité, l’objet hérite de la classe .NET Framework Stream, et fournit des méthodes **ReadByte** et **WriteByte.** Il met également en œuvre des méthodes, telles que **CopyTo** et **Erase**, qui fonctionnent sur des sections d’objets Oracle **LOB.** En revanche, le logiciel client Oracle fournit un certain nombre d’API pour travailler avec le personnage **LOB**s (**CLOB** et **NCLOB**). Toutefois, ces API n'opèrent que sur des caractères complets. En raison de cette différence, le fournisseur de données pour Oracle implémente le support pour **Read** and **ReadByte** pour travailler avec les données UTF-16 d’une manière byte-wise. Cependant, les autres méthodes de l’objet **OracleLob** ne permettent que des opérations à caractère complet.  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
