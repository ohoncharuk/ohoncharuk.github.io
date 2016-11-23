---
layout: post
title:  "Enum to String"
date:   2016-11-22 12:00
categories: Snippets
permalink: /snippets/enum-to-string
---

Sometimes it's necessary to assign sring value up on the enum value. It can be achieved with following workaround.

# Example 

~~~csharp
public class EnumToStringUsingDescription : TypeConverter
{
    public override bool CanConvertFrom(ITypeDescriptorContext context, Type sourceType)
    {
        return (sourceType == typeof(Enum));
    }

    public override bool CanConvertTo(ITypeDescriptorContext context, Type destinationType)
    {
        return (destinationType == typeof(String));
    }

    public override object ConvertFrom(ITypeDescriptorContext context, CultureInfo culture, object value)
    {
        return base.ConvertFrom(context, culture, value);
    }

    public override object ConvertTo(ITypeDescriptorContext context, CultureInfo culture, object value, Type destinationType)
    {
        if (!(destinationType == typeof(String)))
        {
            throw new ArgumentException("Can only convert to string.", "destinationType");
        }

        if (!(value.GetType().BaseType == typeof(Enum)))
        {
            throw new ArgumentException("Can only convert an instance of enum.", "value");
        }

        var name = value.ToString();
        var attrs = value.GetType().GetField(name).GetCustomAttributes(typeof(DescriptionAttribute), false);
        return (attrs.Length > 0) ? ((DescriptionAttribute)attrs[0]).Description : name;
    }
}

[TypeConverter(typeof (EnumToStringUsingDescription))]
public enum TrackStatus
{
    [Description("ACTIVE")]
    Active,
    [Description("PENDING")]
    Pending,
    [Description("HOLD")]
    Hold,
    [Description("DELETED")]
    Deleted
}

var listItems = Enum.GetValues(typeof(TrackStatus)).Cast<TrackStatus>().ToList();


~~~