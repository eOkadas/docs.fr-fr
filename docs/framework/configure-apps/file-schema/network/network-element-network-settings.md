---
title: <network>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: ee60b990bc749dbb9c5d0e7426c57e9392ddf9d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920974"
---
# <a name="network-element-network-settings"></a>\<Network >, élément (paramètres réseau)
Configure les options réseau pour un serveur SMTP (simple mail transport Protocol) externe.  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<network>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`clientDomain`|Spécifie le nom de domaine client à utiliser dans la demande de protocole SMTP initiale pour se connecter au serveur de messagerie SMTP. La valeur par défaut est le nom localhost de l’ordinateur local qui envoie la demande.|  
|`defaultCredentials`|Spécifie si les informations d’identification de l’utilisateur par défaut doivent être utilisées pour accéder au serveur de messagerie SMTP pour les transactions SMTP. La valeur par défaut est `false`.|  
|`enableSsl`|Spécifie si le protocole SSL est utilisé pour accéder à un serveur de messagerie SMTP. La valeur par défaut est `false`.|  
|`host`|Spécifie le nom d’hôte du serveur de messagerie SMTP à utiliser pour les transactions SMTP. Cet attribut n’a pas de valeur par défaut.|  
|`password`|Spécifie le mot de passe à utiliser pour l’authentification auprès du serveur de messagerie SMTP. Cet attribut n’a pas de valeur par défaut.|  
|`port`|Spécifie le numéro de port à utiliser pour se connecter au serveur de messagerie SMTP. La valeur par défaut est 25.|  
|`targetName`|Spécifie le nom du fournisseur de services (SPN) à utiliser pour l’authentification lors de l’utilisation de la protection étendue pour les transactions SMTP. Cet attribut n’a pas de valeur par défaut.|  
|`userName`|Spécifie le nom d’utilisateur à utiliser pour l’authentification auprès du serveur de messagerie SMTP. Cet attribut n’a pas de valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Élément > SMTP (paramètres réseau)](smtp-element-network-settings.md)|Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).|  
  
## <a name="remarks"></a>Notes  
 Certains serveurs SMTP nécessitent que vous vous authentifiez auprès du serveur avant de l’utiliser. Si vous souhaitez vous authentifier à l’aide des informations d’identification réseau par défaut sur votre `defaultCredentials` ordinateur hôte `true`, affectez la valeur à l’attribut. La <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `defaultCredentials` attribut à partir des fichiers de configuration applicables.  
  
 Vous pouvez également utiliser l’authentification de base (un nom d’utilisateur et un mot de passe) pour vous authentifier auprès du serveur SMTP. Pour utiliser cette option, vous devez spécifier un nom d’utilisateur et un mot de passe valides pour le serveur SMTP spécifié.  
  
> [!NOTE]
> L’authentification de base `userName` envoie `password` les valeurs et au serveur non chiffré. Toute personne surveillant le trafic réseau peut afficher vos informations d’identification et les utiliser pour se connecter au serveur. Vous devez envisager d’utiliser un mécanisme d’authentification plus sécurisé, tel que Kerberos ou NT LAN Manager (NTLM). Si `defaultCredentials` est`true`, Kerberos ou NTLM sera utilisé si le serveur prend en charge ces protocoles.  
  
 Les options authentification de base et informations d’identification réseau par défaut s’excluent mutuellement; Si vous affectez `true` à la valeur `defaultCredentials` et spécifiez un nom d’utilisateur et un mot de passe, les informations d’identification réseau par défaut sont utilisées et les données d’authentification de base sont ignorées.  
  
 Pour l’authentification de base si vous `userName`spécifiez un, vous devez `password` également spécifier un pour vous authentifier auprès du serveur de messagerie.  
  
 La <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `userName` attribut à partir des fichiers de configuration applicables. La <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `password` attribut à partir des fichiers de configuration applicables. Aucun `password` attribut n’est normalement entré dans les fichiers de configuration pour des raisons de sécurité.  
  
 L' `clientDomain` attribut modifie le nom de domaine client utilisé dans la demande de protocole SMTP initiale pour un serveur SMTP. L' `clientDomain` attribut peut être défini sur le nom de domaine complet de l’ordinateur local, plutôt que sur le nom localhost qui est utilisé par défaut. Cela offre une meilleure conformité avec les normes de protocole SMTP. La valeur par défaut est le nom localhost de l’ordinateur local qui envoie la demande. La <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `clientDomain` attribut à partir des fichiers de configuration applicables.  
  
 L' `targetName` attribut est utilisé pour l’authentification lors de l’utilisation de la protection étendue. La valeur par défaut se présente sous la forme «\<SMTPSVC/Host > \<», où Host > est le nom d’hôte du serveur de messagerie SMTP. La <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `targetName` attribut à partir des fichiers de configuration applicables.  
  
 L' `enableSsl` attribut spécifie si le protocole SSL est utilisé pour accéder à un serveur de messagerie SMTP. La <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe prend en charge uniquement l’extension de service SMTP pour SMTP sécurisé sur Transport Layer Security, comme défini dans la norme RFC 3207. Dans ce mode, la session SMTP commence sur un canal non chiffré, puis une commande STARTTLS est émise par le client vers le serveur pour basculer vers une communication sécurisée à l’aide de SSL. Pour plus d’informations, consultez RFC 3207 publié par l’IETF (Internet Engineering Task Force).  
  
 Une autre méthode de connexion est l’emplacement où une session SSL est établie au préalable avant l’envoi des commandes de protocole. Cette méthode de connexion est parfois appelée SMTPs et utilise par défaut le port 465. Cette autre méthode de connexion utilisant SSL n’est pas prise en charge actuellement.  
  
 La <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `enableSsl` attribut à partir des fichiers de configuration applicables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
