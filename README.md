### This Discord Bot is possess some commands such as:
* -comparing images 
* -memes 
* -generating random duck images

### Basic command:
* $meme
* $animal_meme
* $duck

Image compare,
Train image compare:
*By sending an image of E2 or SECR32, you can compare them on or another


### Code summary:
* comparing image
```
@bot.command()
async def imagesd(ctx):
    for attachment in ctx.message.attachments:
        await ctx.send(f"Received attachment: {attachment.url}")
        filename = attachment.filename
        await ctx.send(f"Received attachment with filename: {filename}")
        await attachment.save("Saved images/"+filename)

        
        cat_x, prob = detect_b("Saved images/"+filename)

        #convert the keras first
        if prob > 0.5:
            if cat_x == "A":
                await ctx.send("Definetly A")

            elif cat_x == "B":
                await ctx.send("This is SECR B")
```
* Meme image
```
  @bot.command()
async def meme(ctx):
    img_name = random.choice(os.listdir("images"))
    with open(f'images/{img_name}', 'rb') as f:
            picture = discord.File(f)
   
    await ctx.send(file=picture)
```

* Themed Meme image(animal)
```
@bot.command()
async def animal_meme(ctx):
    mlg_name = random.choice(os.listdir("newer"))
    with open(f'newer/{mlg_name}', 'rb') as f:
            picture = discord.File(f)
   # Kita kemudian dapat mengirim file ini sebagai tolok ukur!
    await ctx.send(file=picture)
```
* Image generating(duck)
```
# image source
def get_duck_image_url():    
    url = 'https://random-d.uk/api/random'
    res = requests.get(url)
    data = res.json()
    return data['url']

# generating image
@bot.command('duck')
async def duck(ctx):
    '''Setelah kita memanggil perintah bebek (duck), program akan memanggil fungsi get_duck_image_url'''
    image_url = get_duck_image_url()
    await ctx.send(image_url)
```
