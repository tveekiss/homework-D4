from news.models import *
egor = User.objects.create_user('egor')
sabrina = User.objects.create_user('sabrina') 
egor_author = Author.objects.create(user=egor) 
sabrina_author = Author.objects.create(user=sabrina)  
sport = Category.objects.create(category='Спорт')
games = Category.objects.create(category='Игры')  
health = Category.objects.create(category='здоровье') 
nova = Category.objects.create(category='Новинки')   
post = Post.objects.create(author=egor_author, title='Как устроен процесс похудения И при чем тут спорт', text='Желание похудеть обусловлено не только эстетикой, но и заботой о здоровье. В поисках идеальной для себя массы тела большинство пользуется простой формулой: нужно расходовать больше энергии, чем потреблять. И это действительно так: создается дефицит калорий, организм начинает тратить накопленные запасы, человек худеет. Но этот процесс намного сложнее и полон нюансов, которые стоит принимать во внимание. Рассказываем обо всех тонкостях, которые важно учитывать, чтобы запустить процесс потери веса. ')
post1 = Post.objects.create(author=sabrina_author, title='Хорошие игры, которые вы могли пропустить в январе', text='В новом выпуске вас ждут фэнтезийно-комедийная версия Paper, Please, китайская Diablo IV по «Троецарствию», бюджетная, но красивая вариация Resident Evil, новая гача в стиле Honkai Impact 3rd, симулятор строителя, симулятор бога и даже кооператив о преодолении препятствий с помощью верёвки.')
post2 = Post.objects.create(author=egor_author, position='NW', title='Медведев сыграет в составе команды Европы на Кубке Лэйвера', text='Россиянин Даниил Медведев вошел в состав команды Европы на Кубке Лэйвера, сообщается на официальном сайте турнира. Также в состав сборной Европы, капитаном которой будет бывшая первая ракетка мира швед Бьорн Борг, вошли испанец Карлос Алькарас и немец Александр Зверев. ')  
PostCategory.objects.create(category=sport, past=post) 
PostCategory.objects.create(category=health, past=post) 
PostCategory.objects.create(category=games, past=post1) 
PostCategory.objects.create(category=nova, past=post1) 
PostCategory.objects.create(category=sport, past=post2) 
PostCategory.objects.create(category=nova, past=post2)  
comment1 = Comment.objects.create(post=post, author_of_comment=sabrina, comment_text='Крутоо!!!') 
comment2 = Comment.objects.create(post=post1, author_of_comment=egor, comment_text='Вау!!!')     
comment3 = Comment.objects.create(post=post2, author_of_comment=sabrina, comment_text='Ничего себе!') 
comment4 = Comment.objects.create(post=post2, author_of_comment=egor, comment_text='Вот так!')       
post.like()
post.like()
post.like()
post1.like() 
post1.like()
post1.like()
post1.like()
post2.dislike() 
post2.dislike()
post2.dislike()
post2.dislike()
comment1.like()
comment1.like()
comment1.like()
comment2.like() 
comment2.like()
comment3.like() 
comment4.like() 
comment4.dislike() 
comment4.dislike()
egor_author.update_rating()
sabrina_author.update_rating()
winner = Author.objects.order_by('-user_rating')   
for i in winner:      
    i.user_rating
    i.user.username
post_winner = Post.objects.order_by('-post_rating') 
for i in post_winner[:1]:
    i.date                                          
    i.author.user.username
    i.rating               
    i.title
    i.preview()
Post.objects.all().order_by('-rating')[0].comment_set.values(    
    'comment_date',                                              
    'author_of_comment',
    'comment_rating',
    'comment_text')
