.. currentmodule:: glowcord

API Reference
===============

The following section outlines the API of glowcord's command extension module.

.. _ext_commands_api_bot:

Bots
------

Bot
~~~~

.. attributetable:: glowcord.ext.commands.Bot

.. autoclass:: glowcord.ext.commands.Bot
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, check, check_once, command, event, group, listen

    .. automethod:: Bot.after_invoke()
        :decorator:

    .. automethod:: Bot.before_invoke()
        :decorator:

    .. automethod:: Bot.check()
        :decorator:

    .. automethod:: Bot.check_once()
        :decorator:

    .. automethod:: Bot.command(*args, **kwargs)
        :decorator:
    
    .. automethod:: Bot.event()
        :decorator:

    .. automethod:: Bot.group(*args, **kwargs)
        :decorator:

    .. automethod:: Bot.listen(name=None)
        :decorator:

AutoShardedBot
~~~~~~~~~~~~~~~~

.. attributetable:: glowcord.ext.commands.AutoShardedBot

.. autoclass:: glowcord.ext.commands.AutoShardedBot
    :members:

Prefix Helpers
----------------

.. autofunction:: glowcord.ext.commands.when_mentioned

.. autofunction:: glowcord.ext.commands.when_mentioned_or

.. _ext_commands_api_events:

Event Reference
-----------------

These events function similar to :ref:`the regular events <discord-api-events>`, except they
are custom to the command extension module.

.. function:: glowcord.ext.commands.on_command_error(ctx, error)

    An error handler that is called when an error is raised
    inside a command either through user input error, check
    failure, or an error in your own code.

    A default one is provided (:meth:`.Bot.on_command_error`).

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`
    :param error: The error that was raised.
    :type error: :class:`.CommandError` derived

.. function:: glowcord.ext.commands.on_command(ctx)

    An event that is called when a command is found and is about to be invoked.

    This event is called regardless of whether the command itself succeeds via
    error or completes.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. function:: glowcord.ext.commands.on_command_completion(ctx)

    An event that is called when a command has completed its invocation.

    This event is called only if the command succeeded, i.e. all checks have
    passed and the user input it correctly.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. _ext_commands_api_command:

Commands
----------

Decorators
~~~~~~~~~~~~

.. autofunction:: glowcord.ext.commands.command
    :decorator:

.. autofunction:: glowcord.ext.commands.group
    :decorator:

Command
~~~~~~~~~

.. attributetable:: glowcord.ext.commands.Command

.. autoclass:: glowcord.ext.commands.Command
    :members:
    :special-members: __call__
    :exclude-members: after_invoke, before_invoke, error

    .. automethod:: Command.after_invoke()
        :decorator:

    .. automethod:: Command.before_invoke()
        :decorator:

    .. automethod:: Command.error()
        :decorator:

Group
~~~~~~

.. attributetable:: glowcord.ext.commands.Group

.. autoclass:: glowcord.ext.commands.Group
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, command, error, group

    .. automethod:: Group.after_invoke()
        :decorator:

    .. automethod:: Group.before_invoke()
        :decorator:

    .. automethod:: Group.command(*args, **kwargs)
        :decorator:

    .. automethod:: Group.error()
        :decorator:

    .. automethod:: Group.group(*args, **kwargs)
        :decorator:

GroupMixin
~~~~~~~~~~~

.. attributetable:: glowcord.ext.commands.GroupMixin

.. autoclass:: glowcord.ext.commands.GroupMixin
    :members:
    :exclude-members: command, group

    .. automethod:: GroupMixin.command(*args, **kwargs)
        :decorator:

    .. automethod:: GroupMixin.group(*args, **kwargs)
        :decorator:

.. _ext_commands_api_cogs:

Cogs
------

Cog
~~~~

.. attributetable:: glowcord.ext.commands.Cog

.. autoclass:: glowcord.ext.commands.Cog
    :members:

CogMeta
~~~~~~~~

.. attributetable:: glowcord.ext.commands.CogMeta

.. autoclass:: glowcord.ext.commands.CogMeta
    :members:

.. _ext_commands_help_command:

Help Commands
---------------

HelpCommand
~~~~~~~~~~~~

.. attributetable:: glowcord.ext.commands.HelpCommand

.. autoclass:: glowcord.ext.commands.HelpCommand
    :members:

DefaultHelpCommand
~~~~~~~~~~~~~~~~~~~

.. attributetable:: glowcord.ext.commands.DefaultHelpCommand

.. autoclass:: glowcord.ext.commands.DefaultHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

MinimalHelpCommand
~~~~~~~~~~~~~~~~~~~

.. attributetable:: glowcord.ext.commands.MinimalHelpCommand

.. autoclass:: glowcord.ext.commands.MinimalHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

Paginator
~~~~~~~~~~

.. attributetable:: glowcord.ext.commands.Paginator

.. autoclass:: glowcord.ext.commands.Paginator
    :members:

Enums
------

.. class:: BucketType
    :module: glowcord.ext.commands

    Specifies a type of bucket for, e.g. a cooldown.

    .. attribute:: default

        The default bucket operates on a global basis.
    .. attribute:: user

        The user bucket operates on a per-user basis.
    .. attribute:: guild

        The guild bucket operates on a per-guild basis.
    .. attribute:: channel

        The channel bucket operates on a per-channel basis.
    .. attribute:: member

        The member bucket operates on a per-member basis.
    .. attribute:: category

        The category bucket operates on a per-category basis.
    .. attribute:: role

        The role bucket operates on a per-role basis.

        .. versionadded:: 1.3


.. _ext_commands_api_checks:

Checks
-------

.. autofunction:: glowcord.ext.commands.check(predicate)
    :decorator:

.. autofunction:: glowcord.ext.commands.check_any(*checks)
    :decorator:

.. autofunction:: glowcord.ext.commands.has_role(item)
    :decorator:

.. autofunction:: glowcord.ext.commands.has_permissions(**perms)
    :decorator:

.. autofunction:: glowcord.ext.commands.has_guild_permissions(**perms)
    :decorator:

.. autofunction:: glowcord.ext.commands.has_any_role(*items)
    :decorator:

.. autofunction:: glowcord.ext.commands.bot_has_role(item)
    :decorator:

.. autofunction:: glowcord.ext.commands.bot_has_permissions(**perms)
    :decorator:

.. autofunction:: glowcord.ext.commands.bot_has_guild_permissions(**perms)
    :decorator:

.. autofunction:: glowcord.ext.commands.bot_has_any_role(*items)
    :decorator:

.. autofunction:: glowcord.ext.commands.cooldown(rate, per, type=glowcord.ext.commands.BucketType.default)
    :decorator:

.. autofunction:: glowcord.ext.commands.dynamic_cooldown(cooldown, type=BucketType.default)
    :decorator:

.. autofunction:: glowcord.ext.commands.max_concurrency(number, per=glowcord.ext.commands.BucketType.default, *, wait=False)
    :decorator:

.. autofunction:: glowcord.ext.commands.before_invoke(coro)
    :decorator:

.. autofunction:: glowcord.ext.commands.after_invoke(coro)
    :decorator:

.. autofunction:: glowcord.ext.commands.guild_only(,)
    :decorator:

.. autofunction:: glowcord.ext.commands.dm_only(,)
    :decorator:

.. autofunction:: glowcord.ext.commands.is_owner(,)
    :decorator:

.. autofunction:: glowcord.ext.commands.is_nsfw(,)
    :decorator:

.. _ext_commands_api_context:

Cooldown
---------

.. attributetable:: glowcord.ext.commands.Cooldown

.. autoclass:: glowcord.ext.commands.Cooldown
    :members:

Context
--------

.. attributetable:: glowcord.ext.commands.Context

.. autoclass:: glowcord.ext.commands.Context
    :members:
    :inherited-members:
    :exclude-members: history, typing

    .. automethod:: glowcord.ext.commands.Context.history
        :async-for:

    .. automethod:: glowcord.ext.commands.Context.typing
        :async-with:

.. _ext_commands_api_converters:

Converters
------------

.. autoclass:: glowcord.ext.commands.Converter
    :members:

.. autoclass:: glowcord.ext.commands.ObjectConverter
    :members:

.. autoclass:: glowcord.ext.commands.MemberConverter
    :members:

.. autoclass:: glowcord.ext.commands.UserConverter
    :members:

.. autoclass:: glowcord.ext.commands.MessageConverter
    :members:

.. autoclass:: glowcord.ext.commands.PartialMessageConverter
    :members:

.. autoclass:: glowcord.ext.commands.GuildChannelConverter
    :members:

.. autoclass:: glowcord.ext.commands.TextChannelConverter
    :members:

.. autoclass:: glowcord.ext.commands.VoiceChannelConverter
    :members:

.. autoclass:: glowcord.ext.commands.StoreChannelConverter
    :members:

.. autoclass:: glowcord.ext.commands.StageChannelConverter
    :members:

.. autoclass:: glowcord.ext.commands.CategoryChannelConverter
    :members:

.. autoclass:: glowcord.ext.commands.InviteConverter
    :members:

.. autoclass:: glowcord.ext.commands.GuildConverter
    :members:

.. autoclass:: glowcord.ext.commands.RoleConverter
    :members:

.. autoclass:: glowcord.ext.commands.GameConverter
    :members:

.. autoclass:: glowcord.ext.commands.ColourConverter
    :members:

.. autoclass:: glowcord.ext.commands.EmojiConverter
    :members:

.. autoclass:: glowcord.ext.commands.PartialEmojiConverter
    :members:

.. autoclass:: glowcord.ext.commands.ThreadConverter
    :members:

.. autoclass:: glowcord.ext.commands.GuildStickerConverter
    :members:

.. autoclass:: glowcord.ext.commands.clean_content
    :members:

.. autoclass:: glowcord.ext.commands.Greedy()

.. autofunction:: glowcord.ext.commands.run_converters

Flag Converter
~~~~~~~~~~~~~~~

.. autoclass:: glowcord.ext.commands.FlagConverter
    :members:

.. autoclass:: glowcord.ext.commands.Flag()
    :members:

.. autofunction:: glowcord.ext.commands.flag

.. _ext_commands_api_errors:

Exceptions
-----------

.. autoexception:: glowcord.ext.commands.CommandError
    :members:

.. autoexception:: glowcord.ext.commands.ConversionError
    :members:

.. autoexception:: glowcord.ext.commands.MissingRequiredArgument
    :members:

.. autoexception:: glowcord.ext.commands.ArgumentParsingError
    :members:

.. autoexception:: glowcord.ext.commands.UnexpectedQuoteError
    :members:

.. autoexception:: glowcord.ext.commands.InvalidEndOfQuotedStringError
    :members:

.. autoexception:: glowcord.ext.commands.ExpectedClosingQuoteError
    :members:

.. autoexception:: glowcord.ext.commands.BadArgument
    :members:

.. autoexception:: glowcord.ext.commands.BadUnionArgument
    :members:

.. autoexception:: glowcord.ext.commands.BadLiteralArgument
    :members:

.. autoexception:: glowcord.ext.commands.PrivateMessageOnly
    :members:

.. autoexception:: glowcord.ext.commands.NoPrivateMessage
    :members:

.. autoexception:: glowcord.ext.commands.CheckFailure
    :members:

.. autoexception:: glowcord.ext.commands.CheckAnyFailure
    :members:

.. autoexception:: glowcord.ext.commands.CommandNotFound
    :members:

.. autoexception:: glowcord.ext.commands.DisabledCommand
    :members:

.. autoexception:: glowcord.ext.commands.CommandInvokeError
    :members:

.. autoexception:: glowcord.ext.commands.TooManyArguments
    :members:

.. autoexception:: glowcord.ext.commands.UserInputError
    :members:

.. autoexception:: glowcord.ext.commands.CommandOnCooldown
    :members:

.. autoexception:: glowcord.ext.commands.MaxConcurrencyReached
    :members:

.. autoexception:: glowcord.ext.commands.NotOwner
    :members:

.. autoexception:: glowcord.ext.commands.MessageNotFound
    :members:

.. autoexception:: glowcord.ext.commands.MemberNotFound
    :members:

.. autoexception:: glowcord.ext.commands.GuildNotFound
    :members:

.. autoexception:: glowcord.ext.commands.UserNotFound
    :members:

.. autoexception:: glowcord.ext.commands.ChannelNotFound
    :members:

.. autoexception:: glowcord.ext.commands.ChannelNotReadable
    :members:

.. autoexception:: glowcord.ext.commands.ThreadNotFound
    :members:

.. autoexception:: glowcord.ext.commands.BadColourArgument
    :members:

.. autoexception:: glowcord.ext.commands.RoleNotFound
    :members:

.. autoexception:: glowcord.ext.commands.BadInviteArgument
    :members:

.. autoexception:: glowcord.ext.commands.EmojiNotFound
    :members:

.. autoexception:: glowcord.ext.commands.PartialEmojiConversionFailure
    :members:

.. autoexception:: glowcord.ext.commands.GuildStickerNotFound
    :members:

.. autoexception:: glowcord.ext.commands.BadBoolArgument
    :members:

.. autoexception:: glowcord.ext.commands.MissingPermissions
    :members:

.. autoexception:: glowcord.ext.commands.BotMissingPermissions
    :members:

.. autoexception:: glowcord.ext.commands.MissingRole
    :members:

.. autoexception:: glowcord.ext.commands.BotMissingRole
    :members:

.. autoexception:: glowcord.ext.commands.MissingAnyRole
    :members:

.. autoexception:: glowcord.ext.commands.BotMissingAnyRole
    :members:

.. autoexception:: glowcord.ext.commands.NSFWChannelRequired
    :members:

.. autoexception:: glowcord.ext.commands.FlagError
    :members:

.. autoexception:: glowcord.ext.commands.BadFlagArgument
    :members:

.. autoexception:: glowcord.ext.commands.MissingFlagArgument
    :members:

.. autoexception:: glowcord.ext.commands.TooManyFlags
    :members:

.. autoexception:: glowcord.ext.commands.MissingRequiredFlag
    :members:

.. autoexception:: glowcord.ext.commands.ExtensionError
    :members:

.. autoexception:: glowcord.ext.commands.ExtensionAlreadyLoaded
    :members:

.. autoexception:: glowcord.ext.commands.ExtensionNotLoaded
    :members:

.. autoexception:: glowcord.ext.commands.NoEntryPointError
    :members:

.. autoexception:: glowcord.ext.commands.ExtensionFailed
    :members:

.. autoexception:: glowcord.ext.commands.ExtensionNotFound
    :members:

.. autoexception:: glowcord.ext.commands.CommandRegistrationError
    :members:


Exception Hierarchy
~~~~~~~~~~~~~~~~~~~~~

.. exception_hierarchy::

    - :exc:`~.DiscordException`
        - :exc:`~.commands.CommandError`
            - :exc:`~.commands.ConversionError`
            - :exc:`~.commands.UserInputError`
                - :exc:`~.commands.MissingRequiredArgument`
                - :exc:`~.commands.TooManyArguments`
                - :exc:`~.commands.BadArgument`
                    - :exc:`~.commands.MessageNotFound`
                    - :exc:`~.commands.MemberNotFound`
                    - :exc:`~.commands.GuildNotFound`
                    - :exc:`~.commands.UserNotFound`
                    - :exc:`~.commands.ChannelNotFound`
                    - :exc:`~.commands.ChannelNotReadable`
                    - :exc:`~.commands.BadColourArgument`
                    - :exc:`~.commands.RoleNotFound`
                    - :exc:`~.commands.BadInviteArgument`
                    - :exc:`~.commands.EmojiNotFound`
                    - :exc:`~.commands.GuildStickerNotFound`
                    - :exc:`~.commands.PartialEmojiConversionFailure`
                    - :exc:`~.commands.BadBoolArgument`
                    - :exc:`~.commands.ThreadNotFound`
                    - :exc:`~.commands.FlagError`
                        - :exc:`~.commands.BadFlagArgument`
                        - :exc:`~.commands.MissingFlagArgument`
                        - :exc:`~.commands.TooManyFlags`
                        - :exc:`~.commands.MissingRequiredFlag`
                - :exc:`~.commands.BadUnionArgument`
                - :exc:`~.commands.BadLiteralArgument`
                - :exc:`~.commands.ArgumentParsingError`
                    - :exc:`~.commands.UnexpectedQuoteError`
                    - :exc:`~.commands.InvalidEndOfQuotedStringError`
                    - :exc:`~.commands.ExpectedClosingQuoteError`
            - :exc:`~.commands.CommandNotFound`
            - :exc:`~.commands.CheckFailure`
                - :exc:`~.commands.CheckAnyFailure`
                - :exc:`~.commands.PrivateMessageOnly`
                - :exc:`~.commands.NoPrivateMessage`
                - :exc:`~.commands.NotOwner`
                - :exc:`~.commands.MissingPermissions`
                - :exc:`~.commands.BotMissingPermissions`
                - :exc:`~.commands.MissingRole`
                - :exc:`~.commands.BotMissingRole`
                - :exc:`~.commands.MissingAnyRole`
                - :exc:`~.commands.BotMissingAnyRole`
                - :exc:`~.commands.NSFWChannelRequired`
            - :exc:`~.commands.DisabledCommand`
            - :exc:`~.commands.CommandInvokeError`
            - :exc:`~.commands.CommandOnCooldown`
            - :exc:`~.commands.MaxConcurrencyReached`
        - :exc:`~.commands.ExtensionError`
            - :exc:`~.commands.ExtensionAlreadyLoaded`
            - :exc:`~.commands.ExtensionNotLoaded`
            - :exc:`~.commands.NoEntryPointError`
            - :exc:`~.commands.ExtensionFailed`
            - :exc:`~.commands.ExtensionNotFound`
    - :exc:`~.ClientException`
        - :exc:`~.commands.CommandRegistrationError`
