# minibot
import discord
from discord.ext import commands
from lesson_2 import ran_pass
intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='.', intents=intents)
command_info = [
    "1. random_pass - выводит рандомный пароль (можно самостоятельно указать длину пароля)",
    "2. add - сложение двух чисел",
    "3. spam - спам бот"
]

bot = commands.Bot(command_prefix='Kodland-', intents=intents)

@bot.command()
async def info_help(ctx):
    for i in command_info:
        await ctx.send(i)

@bot.command()
async def random_pass(ctx, len_pass = 10):
    await ctx.send(ran_pass(len_pass))

@bot.command()
async def add(ctx, left: int, right: int):
    """Adds two numbers together."""
    await ctx.send(left + right)

@bot.command()
async def spam(ctx, spam_count=10):
    for i in range(spam_count):
        await ctx.send(f"Ха-ха-ха, заспамил {i+1}")
@bot.command()
async def mem(ctx):
    with open('images/mem1.jpg', 'rb') as f:
        # В переменную кладем файл, который преобразуется в файл библиотеки Discord!
        picture = discord.File(f)
   # Можем передавать файл как параметр!
    await ctx.send(file=picture)

bot.run('MTIyODc2MzQ2NTY4MjkxMTI5Ng.GinLFu.bLSnFjV-n1pdMoFx2BFLa36f70AEUzjnM7-YOE')




