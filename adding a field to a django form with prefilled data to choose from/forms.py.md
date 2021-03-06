**app/forms.py**

    from django import forms
    from django.contrib.auth.forms import UserCreationForm
    from django.contrib.auth.models import Group,User

    county_choices=[
    ('Mombasa','001 Mombasa'),	
    ('Kwale','002 Kwale'),		
    ('Kilifi','003 Kilifi'),		
    ('Tana River','004 Tana River'),	
    ('Lamu','005 Lamu'),		
    ('Taita Taveta','006 Taita–Taveta'),		
    ('Garissa','007 Garissa'),		
    ('Wajir','008 Wajir'),		
    ('Mandera','009 Mandera'),		
    ('Marsabit','010 Marsabit'),	
    ('Isiolo','011 Isiolo'),		
    ('Meru','012 Meru'),		
    ('Tharaka-Nithi','013 Tharaka-Nithi'),	
    ('Embu','014 Embu'),		
    ('Kitui','015 Kitui'),		
    ('Machakos','016 Machakos'),	
    ('Makueni','017 Makueni'),		
    (' Nyandarua','018 Nyandarua'),		
    ('Nyeri','019 Nyeri'),		
    ('Kirinyaga','020 Kirinyaga'),
    ('Murang\'a','021 Murang\'a'),	
    ('Kiambu','022 Kiambu'),		
    ('Turkana','023 Turkana'),		
    ('West Pokot','024 West Pokot'),	
    (' Samburu','025 Samburu'),		
    ('Trans-Nzoia','026 Trans-Nzoia'),	
    ('Uasin Gishu','027 Uasin Gishu'),	
    ('Elgeyo-Marakwet','028 Elgeyo-Marakwet'),	
    ('Nandi','029 Nandi'),		
    ('Baringo','030 Baringo'),		
    ('Laikipia','031 Laikipia'),	
    ('Nakuru','032 Nakuru'),		
    ('Narok','033 Narok'),		
    ('Kajiado','034 Kajiado'),		
    ('Kericho','035 Kericho'),		
    ('Bomet','036 Bomet'),		
    ('Kakamega','037 Kakamega'),		
    ('Vihiga','038 Vihiga'),		
    ('Bungoma','039 Bungoma	'),
    (' Busia','040 Busia'),	
    ('Siaya','041 Siaya'),	
    ('Kisumu','042 Kisumu'),		
    ('Homa Bay','043 Homa Bay'),	
    ('Migori','044 Migori'),		
    ('Kisii','045 Kisii'),	
    ('Nyamira','046 Nyamira'),	
    ('Nairobi','047 Nairobi'),
    ]

    class UserRegisterForm(UserCreationForm):    
        location = forms.CharField(label='county', widget=forms.Select(choices=county_choices))
        email = forms.EmailField()

        class Meta:
            model = User
            fields = ['username', 'email', 'password1', 'password2', 'location']
