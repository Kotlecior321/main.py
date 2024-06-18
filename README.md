import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'Zalogowaliśmy się jako {bot.user}')

@bot.event
async def on_ready():
    print(f'Zalogowaliśmy się jako {bot.user}')

@bot.event
async def on_message(message):
    if message.author == bot.user:
        return
    if message.content.startswith('$hello'):
        await message.channel.send("Cześć!")
    elif message.content.startswith('$bye'):
        await message.channel.send("\\U0001f642")
    elif message.content.startswith('$EKO'):
        await message.channel.send("Możesz na przykład: \n-Nie wyrzucać śmieci gdzie popadnie, \n-segregowa śmieci, \n-jeżeli chcesz segregowanie śmieci uczynic fajniejszym to, \nzrób z kartomów prowizoryczne kosze do koszykówki i rzucaj do nich śmieciami, \n-rozdzielanie różnych materiałów z opakowań po różnych rzeczach, \n-nie wywalanie zakrętek z butelek w przyrodzie, \n-JEŻELI TO CIĘ NIE ZACHĘCIŁO TO JA SIĘ PODDAJE :(")
    else:
        await message.channel.send(message.content)
@bot.command()
async def hello(ctx):
    await ctx.send(f'Cześć, jestem bot{bot.user}!')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)

import discord
@bot.command()
async def mem(ctx):
    with open('images/meme.jpg', 'rb') as f:
        picture = discord.File(f)
    await ctx.send(file=picture)

bot.run("TOKEN_BOTA")
