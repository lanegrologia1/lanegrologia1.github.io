INFORMACION DE LA GUIA

1.-La guía esta creada para los usuarios que desean
y requieren desarrollar su propio BOT discord,
ya sea para su servidor privado o al publico.
Toda la información y ejemplos de esta guía,
estan basadas en la documentación oficial de
Discord.js y DiscordAPI.

2.-Este enlace nos llevara a una pagina para ponerle nombre a al bot
https://discordapp.com/login?redirect_to=%2Fdevelopers%2Fapplications%2F
https://media.discordapp.net/attachments/468579488582860800/516704934423691284/unknown.png?width=623&height=395


3.-Cuntinuamos al siguiente paso y selecionaremos las opciones que idica la flecha
en la image donde dice ID de Cliente cpopiar y guardar bien
https://media.discordapp.net/attachments/468579488582860800/516706744643354642/unknown.png?width=761&height=364

4.-Luego tenemos que copiar el link que generamos y pegarlo en una ventana de nuestro explorador
https://media.discordapp.net/attachments/468579488582860800/516708916415954977/unknown.png?width=761&height=328


5.-Procedemos a autorizar el bot en un servidor, es obligatorio ser administrador
https://media.discordapp.net/attachments/468579488582860800/516709925569953813/unknown.pngCrear una carpeta  en Atomo (Atom)con el nombre de tu bot y  clone estos codigos:




6.-Crear una carpeta  en Atomo (Atom)con el nombre de tu bot y  clone estos codigos:
const Discord = require( "discord.js" );
const client = new Discord.Client();
const config = require( "./config.json" );



    console.log( "Coreano-De-Ascetico ready" );
} );
var prefix = config.prefix;


const messageText = ":deciduous_tree::deciduous_tree::deciduous_tree::deciduous_tree::deciduous_tree:\n"
    + ":deciduous_tree::deciduous_tree::monkey::deciduous_tree::deciduous_tree:\n"
    + ":deciduous_tree::deciduous_tree::deciduous_tree::deciduous_tree::mountain_snow:️\n"
    + ":deciduous_tree::deciduous_tree::hole:️:deciduous_tree::deciduous_tree:\n"
    + ":deciduous_tree::deciduous_tree::deciduous_tree::deciduous_tree::deciduous_tree:\n";

const addMessageAndReactions = ( message ) => {
//    const embed = new Discord.RichEmbed()
//    .setColor( 0xff0000 )
//    .setFooter( messageText );

    message.channel.send( messageText ).then( function( message ) {
        message.react( "🐒" );
    } ).catch( function( error ) {
        console.log( "error:" + error );
    } );
}

client.on( 'messageReactionAdd', ( reaction, user ) => {
    if(reaction.count == 1) {
        const message = reaction.message;
        if(reaction.emoji == "🐒") {
            message.react( "⬅" );
        }
        if(reaction.emoji == "⬅") {
            message.react( "🔼" );
        }
        if(reaction.emoji == "🔼") {
            message.react( "🔽" );
        }
        if(reaction.emoji == "🔽") {
            message.react( "➡" );
        }
    }
    if ( reaction.count < 2 ) {
        return;
    }
    addMessageAndReactions( reaction.message );
} );

client.on( "message", ( message ) => {
    if ( message.content.startsWith( "bot?" ) ) {
        addMessageAndReactions( message );
    }

    if ( message.content.startsWith( prefix + "a" ) ) {
        let img = message.mentions.users.first()
        console.log( img );
        if ( !img ) {
            const embed = new Discord.RichEmbed()
                .setImage( `${message.author.AvatarURL}` )
                .setColor( 0x66b3ff )
                .setFooter( `Avatar de ${message.author.username}#${message.author.discriminator}` );
            message.channel.send( { embed } );
        } else if ( img.avatarURL === null ) {
            const embed = new Discord.RichEmbed
                .setImage( `${message.author.defaultAvatarURL}` )
                .setColor( 0x66b3ff )
                .setFooter( `Avatar de ${message.author.username}#${message.author.discriminator}` );
            message.channel.send( { embed } );
        } else {
            const embed = new Discord.RichEmbed()
                .setImage( `${img.avatarURL}` )
                .setColor( 0x66b3ff )
                .setFooter( `Avatar de ${img.username}#${img.discriminator}` );
            message.channel.send( { embed } );
        };



        const moment = require( "moment" );
        require( `moment-duration-format` );

        const actividad = moment.duration( client.uptime ).format( " D [dias], H [hrs], m [mins], s [secs]" );


        const embed = new Discord.RichEmbed()
            .setColor( 0x66ff66 )

            .setAuthor( `Bot info`, client.user.avatarURL )
            .addField( `Dueño`, `user#0000`, true )
            .addField( `Version`, `1.0.0`, true )
            .addField( `Libreria`, `Discord ^11.2.1 (js)`, true )

            .addField( `Memoria`, `${( process.memoryUsage().heapUsed / 1024 / 1024 ).toFixed( 2 )} MB`, true )
            .addField( `Uptime`, `$(actividad)`, true )
            .addField( `Servidores`, `${client.guilds.size.toLocaleString()}`, true )

            .addField( `Usuarios`, `${client.users.size.toLocaleString()}`, true )
            // .addField( `Canales`, `${client.channel.size.toLocaleString()}`, true )
            .addField( `Conexiones a voz`, `${client.voiceConnections.size}`, true )

        message.channel.send( { embed } );

    }
} );
client.login( config.token );


7.-Crear una carpeta llamada Confg.js y pegar su ID de Cliente
