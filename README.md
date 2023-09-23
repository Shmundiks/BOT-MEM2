import discord
import random
from discord.ext import commands
import os

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'Бот {bot.user} запущен!')

@bot.command()
async def mem(ctx):
    image_name = random.choice(os.listdir("images"))
    with open(f'images/{image_name}', 'rb') as f:
        # В переменную кладем файл, который преобразуется в файл библиотеки Discord!
        picture = discord.File(f)
   # Можем передавать файл как параметр!
    await ctx.send(file=picture)

@bot.command()
async def animal(ctx):
    animals_name = random.choice(os.listdir("Animals"))
    with open(f'Animals/{animals_name}', 'rb') as f:
        
        picture = discord.File(f)
   
    await ctx.send(file=picture)
