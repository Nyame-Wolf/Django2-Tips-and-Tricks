**on users/models.py**

    from django.db import models
    from django.contrib.auth.models import AbstractUser

    class CustomUser(AbstractUser):
        pass


**on users/forms.py**

    from django import forms
    from django.contrib.auth.forms import UserCreationForm, UserChangeForm
    from .models import CustomUser

    class CustomUserCreationForm(UserCreationForm):

        class Meta(UserCreationForm.Meta):
            model = CustomUser
            fields = ('username', 'email')

    class CustomUserChangeFrom(UserChangeForm):

        class Meta:
            model = CustomUser
            fields = ('username', 'email')
        
**On users/admin.py**

    from django.contrib import admin
    from django.contrib.auth import get_user_model
    from django.contrib.auth.admin import UserAdmin

    from .forms import CustomUserCreationForm, CustomUserChangeFrom
    from .models import CustomUser

    class CustomUserAdmin(UserAdmin):
        add_form = CustomUserCreationForm
        form = CustomUserChangeFrom
        model = CustomUser
        list_display = ['email', 'username',]

    admin.site.register(CustomUser, CustomUserAdmin)

