# 一、model
```
from django.db import models


class Place(models.Model):
    name = models.CharField(max_length=50)
    address = models.CharField(max_length=80)

class Restaurant(Place):
    serves_hot_dogs = models.BooleanField(default=False)
    serves_pizza = models.BooleanField(default=False)
```
# 二、serializers
```
from rest_framework import serializers
from .models import Place,Restaurant


class PlaceSer(serializers.ModelSerializer):
    class Meta:
        model = Place
        fields = "__all__"


class RestaurantSer(PlaceSer):
    class Meta:
        model = Restaurant
        fields = "__all__"
```
三、view
```
class Placeview(mixins.CreateModelMixin,
                 mixins.UpdateModelMixin,
                 mixins.ListModelMixin,
                 mixins.RetrieveModelMixin,
                 viewsets.GenericViewSet):

    authentication_classes = []
    permission_classes = []
    queryset = Restaurant.objects.all()
    serializer_class = RestaurantSer
```