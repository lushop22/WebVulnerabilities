# OAuth2

Permite al usuario ganar acceso sin exponer sus credenciales de inicio de sesion a la aplicacion que desea usar. Es mas que todo utilizada para integrar funciones de terceros que requieren acceso a cierta data de la cuenta de un usuario.

## Como funciona Oauth2.0 ?

Originalmente como una forma de compartir acceso a una data especifica entre aplicaciones. Funciona definiendo una serie de interaccioens entre 3 partes distintas, **client application, resource owner, OAuth service proveder**

- Client application -> Website o aplicacion web que quiere acceder a la data del usuario
- Resource owner -> Usuario a cuyos datos quiere acceder la aplicacion.
- OAuth service provider -> Website o aplicacion que tiene la data del usuario y acceso a ella. Compatibles con OAuth otorgando una API para interactuar con un servidor de autorizacion y un servidor de recursos.

Hay multiples formas de implementar el OAuth. Conocidos como OAuth "flows" o "grand types". Nos centraremos en el "authorization code" e "implicit" que son los mas cmunes. Ambos tienen las siguientes etapas.

1. El client application request acceso a un subconjunto de la data del usuario, especificando que grant type quiere usar y que tipo de acceso quiere.

2. Se le solicita al usuario loguears en el OAuth service y que de su consentimiento para el acceso requerido.

3. El client application recibe un unico access token que prueba que tienen permiso del usuario para acceder a la data requerida. Exactamente como funciona varia dependiendo del grant type.

4. El client application usa este access token para hacer llamadas a la API obteniendo data relevante del resource server.

## OAuth Grand Types

Determina la secuencia exacta de pasos que estan involucrados en el OAuth process. Tambien afecta como como la aplicacion cliente se comunica con el OAuth service en cada estado, incluyendo como el access token es enviado. Se referencian como **OAuth flows**

Un OAuth service debe ser configurado para admitir una grant type antes que un client application pueda iniciar el flujo correspondiente. El application client especifica que grant type quiere usar en el request inicial de autorizacion enviado al OAuth service.

## OAuth scopes

Para cada OAuth grand type, el cliente especificara que data quiere acceder y que tipo de operacion quiere hacer. Lo hace usando el scope parameter del authorization request enviado al OAuth service.

Para OAuth basico, el scope por el cual cada client application puede hacer un request access es unico para cada OAuth service. El scope es solo un texto arbitrario, el formato peude variar entre proveedores. Algunos incluso usan un full URI como nombre de scope, similar a un REST API endpoint. Por ejemplo, al solicitar acceso de lectura a la lista de contactos de un usuario, el scope name puede  tomar cualquiera de las siguientes formas dependdiendo del OAuth service usado:

- scope=contacts
- scope=contacts.read
- scope=contact-list-r
- scope=https://oauth-authorization-server.com/auth/scopes/user/contacts.readonly

Cuando se usa el OAuth para autenticacion, el OpenID Connect scope es usado de maera estandar. El scope openid profile le da al client application read access a un predefinido conjunto de informacion basuca del usuario, como email address, username y mas.

## Authorization code grant type.





